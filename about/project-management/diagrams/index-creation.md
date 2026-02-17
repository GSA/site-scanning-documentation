

```mermaid
graph TD;
    A[Source List 1]-- normalized -->D{Formatted Source List 1};
    B[Source List 2]-- normalized -->E{Formatted Source List 2};
    C[Source List 3]-- normalized -->F{Formatted Source List 3};
    D[Source List 1]-- combined -->G{1,2,3 combined};
    E[Source List 2]-- combined -->G{1,2,3 combined};
    F[Source List 3]-- combined -->G{1,2,3 combined};
    G-->H{1+2+3 dedupped};
```


