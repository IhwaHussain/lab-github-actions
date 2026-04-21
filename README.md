# MLOps Pipeline with GitHub Actions & Redis

![CI Build](https://github.com/IhwaHussain/lab-github-actions/actions/workflows/workflow.yml/badge.svg)
[![codecov](https://codecov.io/gh/IhwaHussain/lab-github-actions/branch/master/graph/badge.svg)

**Live Demo:** [portfolio-builder-ihwaashahussain.replit.app/mlops-demo](https://portfolio-builder-ihwaashahussain.replit.app/mlops-demo/)

---

## Overview

An end-to-end CI/CD pipeline built with **GitHub Actions**, **Python Flask**, and **Redis** — demonstrating automated testing, code coverage enforcement, and production-style continuous integration workflows.

Every push and pull request automatically triggers the full test suite. Any PR that drops code coverage below the team threshold is blocked until tests are added to bring it back up — mirroring real production standards.

**97% code coverage achieved.**

---

## What This Demonstrates

- Automated CI/CD pipeline triggered on every pull request
- Redis-backed service layer tested with PyUnit (unittest)
- Code coverage reporting via Codecov — enforced at 90%+ threshold
- Red-green-refactor TDD workflow using `green` and `coverage`
- Containerized development environment using Docker + VS Code Dev Containers
- Reproducible builds across local and CI environments

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3 |
| Web Framework | Flask |
| Database | Redis |
| Testing | PyUnit (unittest), green, coverage |
| CI/CD | GitHub Actions |
| Coverage | Codecov |
| Containerization | Docker |
| Dev Environment | VS Code Dev Containers |

---

## Project Structure

```
├── models.py          # Database model layer using Redis
├── routes.py          # Main Flask service routes
├── test_models.py     # Unit tests for the data model
├── test_service.py    # Unit tests for the service layer
└── .github/
    └── workflows/
        └── workflow.yml   # GitHub Actions CI pipeline
```

---

## Running Locally

### Option 1: Docker + VS Code (Recommended)

```bash
git clone https://github.com/IhwaHussain/lab-github-actions.git
cd lab-github-actions
code .
```

On first open, VS Code will prompt you to reopen in a container. This builds the Docker image and sets up the full development environment automatically.

### Option 2: Local Python

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

You'll also need Redis running locally:

```bash
docker run -d --name redis -p 6379:6379 -v redis:/data redis:alpine
```

Then start the app:

```bash
honcho start
```

---

## Running the Tests

```bash
make test
```

Uses `green` for TDD-style output — passing tests show green, failing tests show red. Coverage is automatically calculated and reported to Codecov.

---

## CI/CD Pipeline

The GitHub Actions workflow (`.github/workflows/workflow.yml`) runs on every push and pull request:

1. Spins up a Redis service container
2. Installs dependencies
3. Runs the full test suite with coverage
4. Reports results to Codecov
5. Fails the build if coverage drops below threshold

This mirrors a real team CI/CD workflow where no code merges without passing tests and maintaining coverage standards.

---

## Live Demo

An interactive demo of the MLOps pipeline is available here:
👉 [portfolio-builder-ihwaashahussain.replit.app/mlops-demo](https://portfolio-builder-ihwaashahussain.replit.app/mlops-demo/)






