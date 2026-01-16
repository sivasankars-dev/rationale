## 🏗️ Architecture Overview

```mermaid
flowchart LR
    Client[Web / Mobile Client]
    LB[Load Balancer]
    Auth[Auth Service]
    Redis[(Redis Cache)]
    DB[(User Database)]
    OAuth[OAuth Providers\n(Google, Apple)]

    Client --> LB
    LB --> Auth

    Auth --> Redis
    Auth --> DB
    Auth --> OAuth

### Architecture notes
- Stateless JWT authentication enables horizontal scaling
- Redis is used for rate limiting and token metadata caching
- OAuth providers are integrated via standard OAuth 2.0 flows
- Load balancer allows seamless scaling of auth service instances