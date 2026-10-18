# Flowchart – Threaded BST Predecessor and Successor 

```mermaid
flowchart TD
    A([Start]) --> B[/Input number of nodes n and their values/]
    B --> C[Create Threaded BST by inserting all nodes]
    C --> D[/Perform inorder traversal and store values/]
    D --> E[For each node, find predecessor and successor]
    E --> F[Display predecessor and successor for every node]
    F --> G[Handle boundary cases]
    G --> H[Compare results with inorder traversal sequence]
    H --> I{Results match with inorder traversal?}

    I -- Yes --> J[/Display "Verification Successful"/]
    I -- No --> K[/Display "Verification Failed"/]

    J --> L([Stop])
    K --> L

    subgraph P["Find Inorder Predecessor"]
        P1{Is it the minimum node?}
        P1 -- Yes --> P2[Predecessor = Not Exists]
        P1 -- No --> P3[Find predecessor using left thread or left subtree]
    end

    subgraph S["Find Inorder Successor"]
        S1{Is it the maximum node?}
        S1 -- Yes --> S2[Successor = Not Exists]
        S1 -- No --> S3[Find successor using right thread or right subtree]
    end

    E -.-> P1
    E -.-> S1

    style A fill:#f5c2e7,stroke:#333
    style L fill:#f5c2e7,stroke:#333
    style B fill:#c8f7c5,stroke:#333
    style D fill:#c8f7c5,stroke:#333
    style C fill:#bde0f7,stroke:#333
    style E fill:#bde0f7,stroke:#333
    style F fill:#bde0f7,stroke:#333
    style H fill:#bde0f7,stroke:#333
    style I fill:#ffd59e,stroke:#333
    style P1 fill:#ffd59e,stroke:#333
    style S1 fill:#ffd59e,stroke:#333
    style J fill:#d9c2f0,stroke:#333
    style K fill:#d9c2f0,stroke:#333
```

