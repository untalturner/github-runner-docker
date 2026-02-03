# GitHub Actions Self-Hosted Runner (Docker Compose - Ephemeral)

Ephemeral Docker-based self-hosted runners for GitHub Actions with Docker-in-Docker (DinD).

## Features
- **Ephemeral**: Auto-deregisters after each job (clean slate).
- **DinD**: Docker socket mount for building/running containers.
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
```
3. Edit `.env`:
- Set `ACCESS_TOKEN` (base).
- Set `REPO_URL` per env.
4. Start runner:
```
docker compose up -d
```
5. Verify:
```
docker logs -f github-runner
```
Check GitHub: Repo/org Settings > Actions > Runners.
