# Federal Website Index Filtering Process Diagram

This diagram illustrates the process outlined in [index_narrowing_steps.md](index_narrowing_steps.md).

```mermaid
flowchart TD
    A["`**Everything We Can Find**
    ~35,000 URLs
    Combined from all data sources`"] --> B["`**Step 1: Deduplicate**
    ~31,000 URLs
    Remove duplicate URLs`"]
    
    B --> C["`**Step 2: Apply Ignore List**
    ~29,000 URLs
    Remove non-public sites
    (staging, login pages, etc.)`"]
    
    C --> D["`**Step 3: Remove Non-Federal Domains**
    ~27,000 URLs
    Remove non-federal, non-.gov,
    and expired domains`"]
    
    D --> E["`**Site Scanning Engine**
    Analyzes Federal Website Index
    Captures data about each URL`"]
    
    E --> F["`**Step 4: Remove Inactive Sites**
    ~14,000 URLs
    Remove inactive sites and
    data files (XML/JSON)`"]
    
    F --> G["`**Step 5: Deduplicate Final URLs**
    ~12,000 URLs
    Remove duplicate Final URLs`"]
    
    G --> H["`**Step 6: Deduplicate Final Websites**
    ~10,000 URLs
    Remove duplicate base websites`"]
    
    %% Styling
    classDef startNode fill:#e1f5fe
    classDef processNode fill:#f3e5f5
    classDef engineNode fill:#fff3e0
    classDef endNode fill:#e8f5e8
    
    class A startNode
    class B,C,D,F,G processNode
    class E engineNode
    class H endNode
    
    %% Add data snapshots as notes
    B -.-> B1["`**Data Snapshots:**
    Combined: combined-dedup.csv
    Removed: dedup-removed.csv`"]
    
    C -.-> C1["`**Data Snapshots:**
    Remaining: remove-ignore-contains.csv
    Removed: ignored-removed-begins.csv
    ignored-removed-contains.csv`"]
    
    D -.-> D1["`**Data Snapshots:**
    Final: site-scanning-target-url-list.csv
    Removed: nonfederal-removed.csv`"]
    
    E -.-> E1["`**Data Snapshots:**
    All snapshot: weekly-snapshot-all.csv`"]
    
    F -.-> F1["`**Data Snapshots:**
    Primary snapshot: weekly-snapshot.csv`"]
    
    G -.-> G1["`**Data Snapshots:**
    Unique URLs: weekly-snapshot-unique-final-urls.csv
    Removed: removed-final-urls.csv`"]
    
    H -.-> H1["`**Data Snapshots:**
    Unique Websites: weekly-snapshot-unique-final-websites.csv
    Removed: removed-final-url-websites.csv`"]
    
    %% Style the data snapshot boxes
    classDef dataBox fill:#f5f5f5,stroke:#999,stroke-dasharray: 5 5
    class B1,C1,D1,E1,F1,G1,H1 dataBox
```

## Process Summary

| Step | Description | Input Count | Output Count | Key Files |
|------|-------------|-------------|--------------|-----------|
| 0 | Everything We Can Find | - | ~35,000 | combined.csv |
| 1 | Deduplicate | ~35,000 | ~31,000 | combined-dedup.csv |
| 2 | Apply Ignore List | ~31,000 | ~29,000 | remove-ignore-contains.csv |
| 3 | Remove Non-Federal Domains | ~29,000 | ~27,000 | site-scanning-target-url-list.csv |
| 4 | Remove Inactive Sites | ~27,000 | ~14,000 | weekly-snapshot.csv |
| 5 | Deduplicate Final URLs | ~14,000 | ~12,000 | weekly-snapshot-unique-final-urls.csv |
| 6 | Deduplicate Final Websites | ~12,000 | ~10,000 | weekly-snapshot-unique-final-websites.csv |

## Key Outputs

- **Federal Website Index**: The result of Step 3 (~27k URLs) - this is what the Site Scanning engine scans
- **Primary Snapshot**: The result of Step 4 (~14k URLs) - most commonly consulted by users
- **Unique Final Website**: The result of Step 6 (~10k URLs) - deduplicated to unique base websites