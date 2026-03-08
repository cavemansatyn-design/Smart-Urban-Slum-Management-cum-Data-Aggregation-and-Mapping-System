# NIVAAS System Architecture

## Overview

NIVAAS follows a **multi-tier architecture** designed for scalability, security, and multi-stakeholder access. The system is structured to support web and mobile clients, with a centralized backend and specialized services for geospatial and analytical workloads.

---

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              CLIENT LAYER                                         │
├─────────────────┬─────────────────┬─────────────────┬───────────────────────────┤
│  Slum Dweller   │  Citizen        │  Nodal Officer  │  Government               │
│  App (Mobile)   │  App (Web/Mob)  │  Dashboard      │  Dashboard                │
│  React Native   │  React          │  React          │  React                    │
└────────┬────────┴────────┬────────┴────────┬────────┴───────────────┬───────────┘
         │                 │                 │                        │
         └─────────────────┴────────┬────────┴────────────────────────┘
                                    │
                         ┌──────────▼──────────┐
                         │   API Gateway       │
                         │   (Rate Limit, Auth)│
                         └──────────┬──────────┘
                                    │
┌───────────────────────────────────▼───────────────────────────────────────────────┐
│                           APPLICATION LAYER                                        │
├─────────────────┬─────────────────┬─────────────────┬─────────────────────────────┤
│  Report Service │  Survey Service │  Case Service   │  Analytics Service           │
│  (CRUD reports) │  (Collect data) │  (Workflow)     │  (Aggregation, Reports)     │
└────────┬────────┴────────┬────────┴────────┬────────┴──────────────┬────────────┘
         │                 │                 │                        │
         └─────────────────┴────────┬────────┴────────────────────────┘
                                    │
┌───────────────────────────────────▼───────────────────────────────────────────────┐
│                           SERVICE LAYER                                             │
├─────────────────┬─────────────────┬─────────────────┬─────────────────────────────┤
│  Geo Service    │  Auth Service   │  Notification   │  AI/Clustering Service      │
│  (Maps, Geocode)│  (JWT, Roles)   │  (Push, Email)  │  (Heatmap, Boundaries)      │
└────────┬────────┴────────┬────────┴────────┬────────┴──────────────┬────────────┘
         │                 │                 │                        │
         └─────────────────┴────────┬────────┴────────────────────────┘
                                    │
┌───────────────────────────────────▼───────────────────────────────────────────────┐
│                           DATA LAYER                                                │
├─────────────────┬─────────────────┬─────────────────┬─────────────────────────────┤
│  PostgreSQL     │  Redis          │  File Storage   │  Google Maps API            │
│  (Primary DB)   │  (Cache, Queue) │  (Images, Docs) │  (Maps, Geocoding)          │
└─────────────────┴─────────────────┴─────────────────┴─────────────────────────────┘
```

---

## Component Descriptions

### Client Layer

| Component | Technology | Purpose |
|-----------|------------|---------|
| Slum Dweller App | React Native | Mobile-first interface for surveys, welfare, emergency |
| Citizen App | React / PWA | Web and mobile reporting with camera & GPS |
| Nodal Officer Dashboard | React | Case management, verification, heatmap view |
| Government Dashboard | React | Analytics, reports, policy insights |

### Application Layer

| Service | Responsibility |
|---------|----------------|
| **Report Service** | Create, read, update citizen reports; attach images and location |
| **Survey Service** | Collect and store slum dweller survey responses |
| **Case Service** | Workflow management—assign, verify, escalate cases |
| **Analytics Service** | Aggregate data, generate reports, power dashboards |

### Service Layer

| Service | Responsibility |
|---------|----------------|
| **Geo Service** | Geocoding, reverse geocoding, map tile serving |
| **Auth Service** | JWT-based authentication, role-based access control |
| **Notification Service** | Push notifications, email alerts |
| **AI/Clustering Service** | Settlement clustering, heatmap generation, boundary detection |

### Data Layer

| Store | Purpose |
|-------|---------|
| **PostgreSQL** | Primary relational data—reports, surveys, users, cases |
| **Redis** | Session cache, rate limiting, job queues |
| **File Storage** | Images, documents (S3-compatible or local) |
| **Google Maps API** | Map rendering, geocoding, routing |

---

## Data Flow

### Report Submission Flow

1. **Citizen** captures image + location → 2. **Client** sends to API Gateway → 3. **Report Service** validates and stores → 4. **Geo Service** enriches with address → 5. **Case Service** creates case, assigns to nodal officer → 6. **Notification Service** alerts officer

### Survey Collection Flow

1. **Slum Dweller** completes survey form → 2. **Survey Service** validates and stores → 3. **Analytics Service** updates aggregates → 4. **Heatmap** refreshes with new data point

### Analytics Flow

1. **Government** requests dashboard → 2. **Analytics Service** queries aggregates (or cache) → 3. **AI Service** provides clustering insights → 4. **Client** renders charts and maps

---

## Security Considerations

- **Authentication**: JWT with refresh tokens; role-based access (citizen, dweller, officer, admin)
- **Authorization**: Resource-level permissions; officers see only assigned regions
- **Data Privacy**: PII encrypted at rest; anonymization for analytics
- **Rate Limiting**: Per-user and per-IP limits on reporting endpoints

---

## Scalability

- **Horizontal scaling**: Stateless API servers behind load balancer
- **Database**: Read replicas for analytics; connection pooling
- **Caching**: Redis for frequently accessed data (heatmap tiles, aggregates)
- **Async jobs**: Background processing for heavy analytics and notifications

---

## Future Technical Implementation

See [docs/future-implementation.md](future-implementation.md) for phased rollout plan.
