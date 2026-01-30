# GitHub Actions Self-Hosted Runner (Docker Compose - Dual Ephemeral)

Ephemeral Docker-based self-hosted runners for GitHub Actions with Docker-in-Docker (DinD). Runs **develop** and **main** runners simultaneously on one host, distinguished by labels.

## Features
- **Ephemeral**: Auto-deregisters after each job (clean slate).
- **DinD**: Docker socket mount for building/running containers.
- **Dual runners**: Separate `develop`/`main` configs via env files.
- **Maven/Java ready**: Works with your microservices workflows.

## Prerequisites
- Docker & Docker Compose v2+.
- GitHub PAT: [Generate](https://github.com/settings/tokens) with `repo` (full) scope.

## Quick Start
1. Clone:
```
git clone https://github.com/untalturner/github-runner-docker.git
cd github-runner-docker
```
2. Copy env files:
```
cp .env.example .env
cp .env.develop.example .env.develop
cp .env.main.example .env.main
```
3. Edit `.env`, `.env.develop`, `.env.main`:
- Set `ACCESS_TOKEN` (base).
- Set `REPO_URL` per env.
4. Start both runners:
```
docker compose up -d
```
5. Verify:
```
docker compose logs -f
```
Check GitHub: Repo/org Settings > Actions > Runners.

## Usage
- **Workflow labels**:
```
yaml
jobs:
 develop-job:
   runs-on: [develop, self-hosted, docker, linux]
 main-job:
   runs-on: [main, self-hosted, docker, linux]
```
- **Single profile**:
```
docker compose --profile develop up -d  # Only develop runner
```