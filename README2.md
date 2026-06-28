```text
src/

├── apps/
│   │
│   ├── web/                          # TypeScript + Next.js
│   ├── admin/                        # TypeScript + Next.js
│   ├── mission-control/              # TypeScript + React desktop-like UI
│   │
│   └── mobile/                       # React Native (later)
│
├── domains/
│   │
│   ├── mission/                      # TypeScript (NestJS)
│   │   ├── api/
│   │   ├── service/
│   │   ├── entities/
│   │   ├── repository/
│   │   ├── events/
│   │   └── tests/
│   │
│   ├── asteroid/                     # TypeScript
│   │   ├── api/
│   │   ├── orbit/
│   │   ├── mining-priority/
│   │   └── tests/
│   │
│   ├── mining/                       # TypeScript
│   │   ├── extraction/
│   │   ├── refinery/
│   │   ├── inventory/
│   │   └── tests/
│   │
│   ├── robotics/                     # TypeScript
│   │   ├── robots/
│   │   ├── navigation/
│   │   ├── task-planner/
│   │   └── tests/
│   │
│   ├── lunar/
│   │   ├── habitats/
│   │   ├── logistics/
│   │   └── tests/
│   │
│   ├── manufacturing/
│   │   ├── fabrication/
│   │   ├── parts/
│   │   └── tests/
│   │
│   └── economy/
│       ├── resource-market/
│       ├── trading/
│       └── tests/
│
├── simulation/
│   │
│   ├── orbital-engine/               # Python
│   │   ├── propagators/
│   │   ├── transfer-planning/
│   │   └── optimization/
│   │
│   ├── physics-engine/               # Python → Rust later
│   │   ├── thermal/
│   │   ├── structural/
│   │   └── collision/
│   │
│   ├── mining-models/                # Python
│   │   ├── extraction-model/
│   │   ├── ore-prediction/
│   │   └── efficiency/
│   │
│   └── ml/
│       ├── anomaly-detection/
│       ├── prediction/
│       └── training/
│
├── shared/
│   │
│   ├── auth/                         # TypeScript
│   ├── dto/
│   ├── types/
│   ├── constants/
│   ├── utilities/
│   ├── event-contracts/
│   └── logging/
│
├── infrastructure/
│   │
│   ├── docker/
│   ├── postgres/
│   ├── redis/
│   ├── rabbitmq/
│   ├── monitoring/
│   └── deployment/
│
├── scripts/                          # TS/Python
│
├── docs/
│   │
│   ├── architecture/
│   ├── api-specs/
│   ├── ADR/
│   └── diagrams/
│
└── tests/
    ├── integration/
    ├── e2e/
    └── load/
```

Preferred languages by area:

| Area                   |             Language |
| ---------------------- | -------------------: |
| Frontend UI            |           TypeScript |
| APIs/services          |           TypeScript |
| Event consumers        |           TypeScript |
| Simulations            |               Python |
| ML/AI                  |               Python |
| Data pipelines         |               Python |
| Heavy physics later    |                 Rust |
| Infrastructure scripts | TypeScript initially |
| Tests                  |  TypeScript + Python |

So the practical daily workflow becomes:

**Day 1**

```text
domains/mining/extraction/
```

Build:

* extraction UI
* extraction API
* extraction DB model
* extraction event

**Day 2**

```text
domains/robotics/task-planner/
```

Build:

* planner UI
* planner service
* planner DB

**Day 3**

Connect:

```text
RobotAssigned
        ↓
TaskPlanner
        ↓
MiningService
        ↓
InventoryUpdate
```
