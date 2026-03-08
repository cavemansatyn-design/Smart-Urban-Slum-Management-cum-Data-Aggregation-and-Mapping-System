# NIVAAS System Workflow

## Overview

This document describes the end-to-end workflows that power NIVAAS—from citizen reporting to government decision-making.

---

## Workflow 1: Citizen Reporting

```
┌──────────┐     ┌──────────────┐     ┌─────────────┐     ┌──────────────┐
│  Citizen │────▶│  Discover   │────▶│  Open App   │────▶│  Report with │
│          │     │  Settlement  │     │             │     │  Photo+Loc   │
└──────────┘     └──────────────┘     └─────────────┘     └──────┬───────┘
                                                                 │
┌──────────┐     ┌──────────────┐     ┌─────────────┐             │
│  Case    │◀────│  Nodal      │◀────│  System     │◀────────────┘
│  Created │     │  Assigned   │     │  Validates  │
└──────────┘     └──────────────┘     └─────────────┘
```

### Steps

1. **Discovery** — Citizen observes illegal settlement or encroachment
2. **App Open** — Launches NIVAAS (web or mobile)
3. **Report** — Captures photo(s), allows GPS location, adds optional description
4. **Validation** — System validates image, location, and required fields
5. **Case Creation** — Report becomes a case in the system
6. **Assignment** — Case auto-assigned to nodal officer based on location/region

---

## Workflow 2: Survey Collection (Slum Dweller)

```
┌──────────────┐     ┌──────────────┐     ┌─────────────┐
│  Dweller     │────▶│  Access      │────▶│  Complete   │
│  Registers   │     │  Survey Form │     │  Demographics│
└──────────────┘     └──────────────┘     └──────┬──────┘
                                                 │
┌──────────────┐     ┌──────────────┐             │
│  Heatmap     │◀────│  Data       │◀────────────┘
│  Updated     │     │  Stored     │
└──────────────┘     └──────────────┘
```

### Steps

1. **Registration** — Dweller creates account (optional for anonymous surveys)
2. **Survey Access** — Navigates to survey section
3. **Completion** — Fills demographic, living condition, and welfare eligibility info
4. **Storage** — Data saved to database with location
5. **Visualization** — Heatmap and analytics updated with new data point

---

## Workflow 3: Nodal Officer Verification

```
┌──────────────┐     ┌──────────────┐     ┌─────────────┐
│  Officer     │────▶│  View        │────▶│  Verify     │
│  Logs In     │     │  Assigned    │     │  On-Ground  │
└──────────────┘     └──────────────┘     └──────┬──────┘
                                                  │
                    ┌──────────────┐               │
                    │  Update      │◀──────────────┤
                    │  Status      │               │
                    └──────┬───────┘               │
                           │                       │
              ┌────────────┴────────────┐          │
              ▼                         ▼          │
       ┌─────────────┐           ┌─────────────┐   │
       │  Escalate   │           │  Close      │   │
       │  to Gov     │           │  Case       │   │
       └─────────────┘           └─────────────┘   │
```

### Steps

1. **Login** — Officer authenticates with credentials
2. **Case Queue** — Views list of assigned cases (filterable by status, priority)
3. **Verification** — Visits location, confirms or disputes report
4. **Status Update** — Marks as verified, disputed, or needs escalation
5. **Escalation** — Sends to government for policy/relocation decision
6. **Closure** — Case closed when resolved

---

## Workflow 4: Government Analytics & Decision

```
┌──────────────┐     ┌──────────────┐     ┌─────────────┐
│  Gov User    │────▶│  View        │────▶│  Analyze    │
│  Logs In     │     │  Dashboard   │     │  Reports    │
└──────────────┘     └──────────────┘     └──────┬──────┘
                                                  │
                    ┌──────────────┐               │
                    │  Export      │◀──────────────┤
                    │  / Share     │               │
                    └──────┬───────┘               │
                           │                       │
              ┌────────────┴────────────┐          │
              ▼                         ▼          │
       ┌─────────────┐           ┌─────────────┐   │
       │  Policy     │           │  Relocation │   │
       │  Planning   │           │  Planning   │   │
       └─────────────┘           └─────────────┘   │
```

### Steps

1. **Login** — Government user authenticates
2. **Dashboard** — Views heatmaps, trend charts, summary metrics
3. **Reports** — Drills down into regional or settlement-specific data
4. **Export** — Generates PDF/Excel for meetings
5. **Decision** — Uses data for policy, relocation, or welfare planning

---

## Cross-Cutting Workflows

### Emergency Flow

- **Dweller** or **Officer** triggers emergency button
- System sends alert to nodal officers in region
- Location shared for rapid response
- Logged for audit

### Welfare Integration Flow

- **Dweller** checks eligibility for schemes
- System matches survey data with scheme criteria
- Displays applicable schemes and application links
- Tracks application status (future)

---

## State Diagram: Case Lifecycle

```
     [New] ──▶ [Assigned] ──▶ [In Verification] ──▶ [Verified]
                                                           │
                                                           ├──▶ [Escalated]
                                                           │
                                                           └──▶ [Closed]
```

| State | Description |
|-------|-------------|
| **New** | Report submitted, not yet assigned |
| **Assigned** | Assigned to nodal officer |
| **In Verification** | Officer is verifying on-ground |
| **Verified** | Confirmed as valid settlement/encroachment |
| **Escalated** | Sent to government for action |
| **Closed** | Resolved or invalid |

---

## Integration Points

| External System | Purpose |
|-----------------|---------|
| Google Maps API | Geocoding, map display, boundaries |
| Government Welfare Portals | Scheme eligibility, application links |
| SMS/Push Gateways | Notifications to users |
| File Storage | Image and document storage |
