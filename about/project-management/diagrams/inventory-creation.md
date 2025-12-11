```mermaid
block-beta
        columns 1
          block:ID
            A["Agency A website inventory"]
            B["Agency B website inventory"]
            C["Agency C website inventory"]
          end
          space
            D["Harvester combines inventories"]
          end
          space
            E["Public Website Inventory"]
          A --> D
          B --> D
          C --> D
          E --> D
          style B fill:#d6dAdding,stroke:#333,stroke-width:4px
```
