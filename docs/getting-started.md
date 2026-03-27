# Getting Started

Welcome to the test documentation project.

## Prerequisites

- Python 3.12+
- Docker (optional)
- A Confluence Cloud account

## Quick Start

1. Clone the repository
2. Install dependencies: `pip install -r requirements.txt`
3. Run the app: `uvicorn app.main:app --reload`

## Architecture

See [Architecture Overview](./architecture.md) for the system design.

## Configuration

| Variable | Required | Description |
|----------|----------|-------------|
| `GITHUB_APP_ID` | Yes | Your GitHub App ID |
| `CONFLUENCE_URL` | Yes | Confluence base URL |
| `WEBHOOK_SECRET` | Yes | Webhook signing secret |
