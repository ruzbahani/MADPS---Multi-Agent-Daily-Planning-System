# MADPS - Multi-Agent Daily Planning System

An intelligent multi-agent system for personalized daily task scheduling with adaptive replanning.

## Team

- **Ali Mohammadi Ruzbahani** [30261140] - [@ruzbahani](https://github.com/ruzbahani)
- **Shuvam Agarwala** [30290444] - [@ShuvamAgarwala](https://github.com/ShuvamAgarwala)

**Course:** SENG 696 - Agent-Based Software Engineering  
**Instructor:** Professor Behrouz Far  
**University of Calgary** | Fall 2025

## Overview

MADPS uses a three-agent architecture to generate optimal daily schedules that respect constraints, align with user energy patterns, and adapt rapidly to disruptions.

### Core Agents

| Agent | Responsibility |
|-------|---------------|
| **User Profile Agent (UPA)** | Learns energy patterns and preferences from user feedback |
| **Task Management Agent (TMA)** | Manages task lifecycle, validates dependencies (DAG) |
| **Planning & Adaptation Agent (PAA)** | Generates schedules using GA, handles fast replanning |

### Key Features

- ⚡ Fast replanning: p50 ≤ 150ms, p95 ≤ 500ms
- 🎯 Zero hard-constraint violations (deadlines, dependencies)
- 🧠 Personalized scheduling based on learned energy curves
- 🔄 Two-tier adaptation: local repair + global GA optimization
- 📊 Explainable AI with scheduling rationales

## Architecture

```
Logger/Monitor
     │
     ├── UPA ──┐
     ├── PAA ──┼── Message Bus ──── UI/Frontend
     └── TMA ──┘
```

**Design Methodology:** GAIA (Goals, Roles, Interactions, Services, Acquaintance)  
**Communication:** FIPA-compliant ACL messages (REQUEST, PROPOSE, INFORM, ACCEPT/REJECT)

## Technology Stack

- **Agent Framework:** JADE (Java Agent Development Framework)
- **Backend:** PHP 8.0+, MySQL 8.0
- **Frontend:** HTML5, CSS3, JavaScript (ES6+)
- **Communication:** FIPA-ACL via REST API
- **Testing:** PHPUnit, Jest

## Installation

```bash
# Clone repository
git clone https://github.com/ruzbahani/MADPS---Multi-Agent-Daily-Planning-System.git
cd MADPS---Multi-Agent-Daily-Planning-System

# Setup MySQL database
mysql -u root -p < database/schema.sql

# Configure backend
cd backend
cp config.example.php config.php
# Edit config.php with your MySQL credentials

# Setup JADE agents
cd ../agents
# Configure JADE platform
java -cp jade.jar jade.Boot -gui

# Start web server
cd ../frontend
php -S localhost:8080
```

## Usage

```bash
# Start JADE agent platform
cd agents
java -cp jade.jar jade.Boot -gui -agents "UPA:UserProfileAgent;TMA:TaskManagementAgent;PAA:PlanningAgent"

# Start PHP backend server
cd backend
php -S localhost:8080

# Access web interface
# Open browser: http://localhost:8080
```

**Web Interface:**
- Create tasks via web form
- View daily schedule in calendar
- Handle disruptions with drag-and-drop
- Provide feedback via rating buttons

## Performance Targets

| Metric | Target | Status |
|--------|--------|--------|
| Initial plan (≤40 tasks) | ≤ 2s | 🔄 In Dev |
| Local replan (p50) | ≤ 150ms | 🔄 In Dev |
| Local replan (p95) | ≤ 500ms | 🔄 In Dev |
| Constraint violations | 0 | 🔄 In Dev |
| Energy alignment | Week↑ | 🔄 In Dev |

## Documentation

- **[Report 1A: System Specification](docs/reports/Report-1A-System-Specification.pdf)** ✅
- **[Report 1B: GAIA Design](docs/reports/Report-1B-GAIA-Design.pdf)** ✅

## Project Roadmap

- [x] Phase 1: Specification & Design (Reports 1A, 1B)
- [ ] Phase 2: Agent Implementation (SPADE)
- [ ] Phase 3: Optimization & Learning
- [ ] Phase 4: UI Development (React)
- [ ] Phase 5: Testing & Evaluation
- [ ] Phase 6: Final Report & Presentation

## Testing

```bash
# PHP backend tests
cd backend/tests
phpunit --coverage-html coverage/

# JavaScript frontend tests
cd frontend/tests
npm test

# JADE agent tests
cd agents/tests
java -cp junit.jar:jade.jar org.junit.runner.JUnitCore AgentTestSuite
```

## License

MIT License - See [LICENSE](LICENSE)

**Academic Project:** SENG 696 @ University of Calgary (Fall 2025)

## Contact

- **Ali Mohammadi:** ali.mohammadiruzbaha@ucalgary.ca
- **Shuvam Agarwala:** shuvam.agarwala@ucalgary.ca
- **Repository:** https://github.com/ruzbahani/MADPS---Multi-Agent-Daily-Planning-System
