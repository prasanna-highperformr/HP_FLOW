# Service Architecture Diagram

The following Mermaid diagram illustrates the architecture where the TweetHP main server interacts with three services: Auth-Service, Big Brain Service, and Profile-Analyzer-Service. These services are only accessible via the TweetHP main server.

```mermaid
graph TD
    A[TweetHP - Main Server] -->|Interacts with| B[Auth-Service]
    A -->|Interacts with| C[Big Brain Service]
    A -->|Interacts with| D[Profile-Analyzer-Service]
    B -->|Accessible only via| A
    C -->|Accessible only via| A
    D -->|Accessible only via| A
```