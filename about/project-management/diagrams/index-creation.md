

```mermaid
graph TD;
    A[Source List 1]-- normalized -->D{Source List 1, formatted};
    B[Source List 2]-- normalized -->E{Source List 2, formatted};
    C[Source List 3]-- normalized -->F{Source List 3, formatted};
    D[Source List 1]-- combined -->G{1,2,3 combined};
    E[Source List 2]-- combined -->G{1,2,3 combined};
    F[Source List 3]-- combined -->G{1,2,3 combined};
    G-->H{1+2+3 dedupped};
```


