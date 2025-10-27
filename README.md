# Agents Reno - Multi-Agent Portfolio System

A multi-agent AI system for automated sector discovery, analysis, ticker ranking, portfolio strategy, and risk management using Codex AI.

## Overview

This system implements a 5-stage agent pipeline:
1. **Sector Discovery**: Recommends 3-5 promising sectors based on market trends
2. **Sector Analysis**: Deep analysis of selected sector (news, filings, flows)
3. **Ticker Ranking**: Finds and ranks tickers within the sector
4. **Portfolio Strategy**: Generates 3 scenarios (conservative, neutral, aggressive)
5. **Risk Management**: Validates constraints and provides risk warnings

## Project Structure

```
agents-reno/
├── agents/
│   ├── core/           # Codex client, orchestrator, memory
│   ├── stages/          # 5 agent implementations
│   ├── data/collectors/ # Data collection (news, price, SEC, ETF)
│   └── utils/           # Prompts, validators
├── config/              # constraints.yml, sectors.yml
├── reports/              # Generated reports
└── tests/                # Unit tests
```

## Setup

### Prerequisites

- Python 3.11+
- Poetry (install via: `curl -sSL https://install.python-poetry.org | python3 -`)

### Installation

1. Clone the repository:
```bash
cd agents-reno
```

2. Install dependencies:
```bash
poetry install
```

3. Set up environment variables:
```bash
cp .env.example .env
# Edit .env and add your API keys:
# - OPENAI_API_KEY (for Codex)
# - NEWS_API_KEY
# - SEC_API_KEY
```

4. Activate Poetry shell:
```bash
poetry shell
```

## Usage

### Run Full Pipeline

```bash
python main.py run
```

### With Preset Sector

```bash
python main.py run --sector aerospace
```

### Test Individual Stage

```bash
python main.py test-stage sector_discovery
```

## API Keys Required

- **Codex AI**: [OpenAI Dashboard](https://platform.openai.com/api-keys)
- **NewsAPI**: [newsapi.org](https://newsapi.org/register)
- **SEC API**: [sec-api.io](https://sec-api.io/register)

## Development

### Run Tests

```bash
poetry run pytest
```

### Format Code

```bash
poetry run black .
poetry run ruff check --fix .
```

### Type Checking

```bash
poetry run mypy agents/
```

## License

MIT

