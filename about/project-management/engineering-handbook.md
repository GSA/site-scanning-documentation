# Site Scanning Engineer's Handbook

## Intent

This handbook is intended to be a practical guide to common tasks that the Site
Scanning program's engineer will be expected to perform.

## Important GitHub Repositories

The following GitHub repositories contain code that runs on a continual basis
by way of scheduled GitHub Action workflows:

- [site-scanning-engine](https://github.com/GSA/site-scanning-engine)
- [federal-website-index](https://github.com/GSA/federal-website-index)
- [site-scanning-analysis](https://github.com/GSA/site-scanning-analysis)
- [site-scanning-snapshots](https://github.com/GSA/site-scanning-snapshots)

The remainder of this document will focus on the scan engine proper. Details as
to when routines in the repositories listed above run are in listed the
[site-scanning-documentation](https://github.com/GSA/site-scanning-documentation)
repository's [schedule](https://github.com/GSA/site-scanning-documentation/blob/main/pages/schedule.md)
page.

## The Architecture of the Scan Engine

The site scanning engine was built using the [NestJS](https://nestjs.com/)
framework. There are three apps:

- `apps/api`: exposes a web API that users can call to retrieve scan results.
- `apps/cli`: exposes a command-line interface that lets the Site Scanning
  engineer perform tasks via the command line locally or via GitHub Actions.
- `apps/scan-engine`: when the `.github/workflows/deploy.yml` action runs, this
  app is bootstraped and started along with the API. It watches the message
  queue (configured in `libs/message-queue` and `libs/queue`) and starts
  processing jobs if the queue has one or more jobs in it.

These apps refer to [libraries](https://docs.nestjs.com/cli/libraries) in the
`lib/` directory. These libraries encapsulate functionality for database access
and other concerns.

## The Past Two Years in Review

The architecture of the site scanning engine as described above has been solidly
in place since May 2022. Below is a list of significant additions made from
May 2022 through April 2024:

- `libs/core-scanner/src/pages/accessibility`
- `libs/core-scanner/src/pages/performance`
- `libs/core-scanner/src/scans/login.ts`
- `libs/core-scanner/src/scans/mobile.ts`
- `libs/core-scanner/src/scans/required-links.ts`
- `libs/core-scanner/src/scans/search.ts`
- `libs/security-data`: this module fetches security-related data from a
  publicly hosted CSV file, saves it locally, and serves as a gateway for
  `libs/core-scanner/src/core-scanner.service.ts` to access that
  security-related data.

## On the Horizon (Summer 2024)

The Site Scanning team just finished adding a number of new scans, including
accessibility, performance, and security, at the behest of the [Office of
Management and Budget (OMB)](https://www.whitehouse.gov/omb/). Throughout the
rest of the year, the team anticipates receiving feedback and questions from
stakeholders as the data collected by the scan engine circulates throughout
various agencies.

## Common Tasks

### Adding New Scans

In Site Scanning parlance, a "scan" is a discrete set of functionality that
examines Puppeteer pages and/or HTTP Response objects in order to collect one
or more related data points.

For example, the `libs/core-scanner/src/scans/mobile.ts` module exposes a single
function that takes a logger and a Puppeteer page as arguments and returns a
Promise that yields an object literal with one property on resolution.

```TypeScript
// defined in entities/scan-data.entity.ts
export type MobileScan = {
  viewportMetaTag: boolean;
};

// defined in libs/core-scanner/src/scans/mobile.ts
export const buildMobileResult = async (
  logger: Logger,
  page: Page,
): Promise<MobileScan> => {
  const viewportMetaTag = await getHasViewportMetaTag(page);

  return {
    viewportMetaTag,
  };
};
```

Generally, scans will use one or more helper functions, such as
`getHasViewportMetaTag` in the example above.

You may be wondering: what is the difference between "scans" and "pages"? The
`core-scanner` library's structure indicates that these two are distinct from
one another. In a nutshell, the modules in `scans/` are used by
`pages/primary.ts`, which is just a thin wrapper that passes these modules
whatever they need to do their work.

### Modifying Scans

Sometimes the team needs to update how a datapoint in a given scan is collected.
For example, the scoring algorithms contained in `libs/core-scanner/src/scans/uswds.ts`
may need to be adjusted.

### Exporting Data for Internal Review

In order to collect data for new and modified scans at scale, the Site Scanning
engineer pushes changes to production, lets the scans rerun, and then accesses
the site scanning engine's PostgreSQL database by way of local scripts.

### Exposing New Fields to the Public via API and Snapshot

When the time comes to expose new and modified scan data, the Site Scanning
engineer will make corresponding changes to the `CoreResult` entity and the
snapshot module (`libs/snapshot`).

#### CoreResult Entity

Properties of the `CoreResult` entity are exposed via the API by removing the
`Exclude` [class-transformer](https://github.com/typestack/class-transformer)
decorator. For example, if we want to expose the field below, we would remove
the third line.

```TypeScript
@Column({ nullable: true })
@Expose({ name: 'accessibility_results' })
@Exclude()
accessibilityResults?: string;
```

Suffice to say, when adding new properties to the `CoreResult` entity ahead of
collecting updated scan data, the Site Scanning engineer should use the
`Exclude` decorator initially, and then remove it once the property is ready to
be open.

#### Snapshot Module

The `CoreResult` entity's static `snapshotColumnOrder` property specifies which
fields will be included in the CSV and JSON snapshots that the scan engine
produces. To include a new property in the snapshots, add it to the appropriate
place in the `snapshotColumnOrder` array and then update related unit tests in
`libs/snapshot`.

### Troubleshooting Scan Results

Oftentimes stakeholders or other members of the team will notice oddities and
anomalies in the scan data by way of analyzing the CSV snapshot in Google Drive.
Troubleshooting these sorts of issues tends to involve making debugging changes
to the codebase, rebuilding the app, and running the scan engine against one or
more target URLs where the issue crops up--all of this happens in the Site
Scanning engineer's **local** environment.

## Potentially Useful Scripts

The scripts below fetch information concerning active cloud.gov deployments. To run them, you must log in to cloud.gov from the command line as
follows:

```shell
cf login -a https://api.fr.cloud.gov --sso
```

View a list of how many cloud.gov tasks are in various states:

```bash
#!/usr/bin/env bash

set -e

if [ -z "$1" ]; then
    echo "Error: No space argument provided. For a list of spaces, run 'cf spaces'."
    echo "Usage: $0 <space_name>"
    exit 1
fi

if [[ "$1" != "prod" && "$1" != "dev" && "$1" != "staging" ]]; then
    echo "Error: Invalid space argument '$1'."
    echo "Valid spaces:"
    cf spaces
    exit 1
fi

cf target -o gsatts-sitescan -s "$1"
APP_GUID=$(cf app site-scanner-consumer --guid)
# get memory usage of running tasks for your app
cf curl "/v3/apps/$APP_GUID/tasks" | jq '.resources[] | select (.state=="RUNNING")'

# Define the states you're interested in
STATES=("SUCCEEDED" "FAILED" "RUNNING" "PENDING" "CANCELING")

# Loop through each state and count the occurrences
for state in "${STATES[@]}"; do
    count=$(cf curl "/v3/apps/$APP_GUID/tasks" | jq --arg state "$state" '[.resources[] | select(.state==$state)] | length')
    echo "$state=$count"
done
```

View a list of all cloud.gov tasks in the `RUNNING`, `PENDING`, `CANCELING`, and
`FAILED` states:

```bash
#!/usr/bin/env bash

set -e

# Step 1: Obtain the organization's usage summary for all applications.
ORG_GUID=$(cf org gsatts-sitescan --guid)
USAGE_SUMMARY=$(cf curl /v3/organizations/$ORG_GUID/usage_summary | jq .usage_summary)

# Step 2: Iterate through each space, then iterate through each app in a given
# space in order to tally (a) the total number of app instances, and (b) the
# total amount of memory in mb for all app instances.
SPACE_GUIDS=$(cf curl /v3/spaces?organization_guids="${ORG_GUID}" | jq -r .resources[].guid)
TOTAL_INSTANCES=0
TOTAL_APP_MEM_IN_MB=0

for space_guid in $SPACE_GUIDS; do
    echo "Space GUID: $space_guid"
    APP_GUIDS=$(cf curl /v3/apps?space_guids="${space_guid}" | jq -r .resources[].guid)
    for app_guid in $APP_GUIDS; do
        echo "App GUID: $app_guid"

        # Tally app instances.
        instances=$(cf curl v3/apps/${app_guid}/processes | jq -r .resources[].instances)
        TOTAL_INSTANCES=$((TOTAL_INSTANCES + $instances))

        # Tally app instances memory_in_mb.
        memory_in_mb=$(cf curl v3/apps/${app_guid}/processes | jq -r .resources[].memory_in_mb)
        memory_for_all_instances=$((instances * memory_in_mb))
        TOTAL_APP_MEM_IN_MB=$((TOTAL_APP_MEM_IN_MB + $memory_for_all_instances))

        running_tasks=$(cf curl /v3/apps/$app_guid/tasks | jq '.resources[] | select (.state=="RUNNING")')
        if [ -z "$running_tasks" ]; then
            echo "No tasks are currently running"
        else
            echo "$running_tasks"
        fi

        pending_tasks=$(cf curl /v3/apps/$app_guid/tasks | jq '.resources[] | select (.state=="PENDING")')
        if [ -z "$pending_tasks" ]; then
            echo "No tasks are currently pending"
        else
            echo "$pending_tasks"
        fi

        canceling_tasks=$(cf curl /v3/apps/$app_guid/tasks | jq '.resources[] | select (.state=="CANCELING")')
        if [ -z "$canceling_tasks" ]; then
            echo "No tasks are currently canceling"
        else
            echo "$canceling_tasks"
        fi

        failed_tasks=$(cf curl /v3/apps/$app_guid/tasks | jq '.resources[] | select (.state=="FAILED")')
        if [ -z "$failed_tasks" ]; then
            echo "No tasks have failed"
        else
            echo "$failed_tasks"
        fi
    done
done

# Print Step 1 results.
echo $USAGE_SUMMARY

# Print Step 2 results.
echo $TOTAL_INSTANCES: total instances
echo $TOTAL_APP_MEM_IN_MB: total memory_in_mb for all app instances
```
