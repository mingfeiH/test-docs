# Setup Guide

## Local Development

Follow these steps to set up your local development environment.

### 1. Clone and Install

```bash
git clone https://github.com/your-org/docsync.git
cd docsync
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 2. Configure Environment

Copy the example environment file:

```bash
cp .env.example .env
```

Edit `.env` with your credentials.

### 3. Run

```bash
uvicorn app.main:app --reload --port 3000
```

## Related

- [Getting Started](../getting-started.md)
- [Architecture](../architecture.md)
