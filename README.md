# Pangolin Skills

Python toolkit and [OpenClaw](https://clawhub.ai) skills for [Pangolin](https://www.pangolinfo.com) APIs. Two independent skills: Google SERP + AI Overviews, and Amazon product scraping.

## Skills

### Pangolinfo AI SERP

Google search results + AI Overviews via Pangolin APIs, with multi-turn follow-ups.

- **Install:** [clawhub.ai/pangolinfo/pangolinfo-ai-serp](https://clawhub.ai/pangolinfo/pangolinfo-ai-serp)
- **Skill:** `skills/pangolinfo-ai-serp/`

```bash
# AI Mode search (default)
python3 skills/pangolinfo-ai-serp/scripts/pangolin.py --q "what is quantum computing"

# Standard SERP with screenshot
python3 skills/pangolinfo-ai-serp/scripts/pangolin.py --q "best databases 2025" --mode serp --screenshot

# Multi-turn follow-up
python3 skills/pangolinfo-ai-serp/scripts/pangolin.py --q "kubernetes" --follow-up "how to deploy"
```

### Pangolinfo Amazon Scraper

Amazon product data scraping: products, keywords, categories, rankings, reviews.

- **Install:** [clawhub.ai/pangolinfo/pangolinfo-amazon-scraper](https://clawhub.ai/pangolinfo/pangolinfo-amazon-scraper)
- **Skill:** `skills/pangolinfo-amazon-scraper/`

```bash
# Product detail by ASIN
python3 skills/pangolinfo-amazon-scraper/scripts/pangolin.py --content B0DYTF8L2W --site amz_us

# Keyword search
python3 skills/pangolinfo-amazon-scraper/scripts/pangolin.py --q "wireless mouse" --site amz_us

# Critical reviews
python3 skills/pangolinfo-amazon-scraper/scripts/pangolin.py --content B00163U4LK --mode review --filter-star critical
```

## Setup

```bash
export PANGOLIN_TOKEN="your-token"
# Or:
export PANGOLIN_EMAIL="your@email.com"
export PANGOLIN_PASSWORD="your-password"
```

> Tokens are permanent and cached at `~/.pangolin_token`.

## Self-Test

```bash
# Test AI SERP skill
bash skills/pangolinfo-ai-serp/scripts/self_test.sh

# Test Amazon Scraper skill
bash skills/pangolinfo-amazon-scraper/scripts/self_test.sh
```

## Requirements

- Python 3.8+ (stdlib only, zero dependencies)
- [Pangolin](https://www.pangolinfo.com) account with credits

## Structure

```
.
├── README.md
└── skills/
    ├── pangolinfo-ai-serp/              # Google SERP + AI Overviews
    │   ├── SKILL.md                     # Skill definition
    │   ├── scripts/
    │   │   ├── pangolin.py              # CLI client
    │   │   └── self_test.sh             # Self-test script
    │   └── references/
    │       ├── ai-mode-api.md           # AI Mode API reference
    │       ├── ai-overview-serp-api.md  # SERP API reference
    │       ├── error-codes.md           # Error codes
    │       ├── output-schema.md         # Output JSON schema
    │       └── examples/
    │           ├── ai-mode-example.json # Example output
    │           └── serp-example.json    # Example output
    ├── pangolinfo-amazon-scraper/       # Amazon Scraper
    │   ├── SKILL.md                     # Skill definition
    │   ├── scripts/
    │   │   ├── pangolin.py              # CLI client
    │   │   └── self_test.sh             # Self-test script
    │   └── references/
    │       ├── amazon-api.md            # Amazon API reference
    │       ├── error-codes.md           # Error codes
    │       ├── output-schema.md         # Output JSON schema
    │       └── examples/
    │           ├── keyword-search-example.json
    │           └── product-detail-example.json
```

## Links

- [Pangolin Homepage](https://www.pangolinfo.com)
- [AI SERP on ClawHub](https://clawhub.ai/pangolinfo/pangolinfo-ai-serp)
- [Amazon Scraper on ClawHub](https://clawhub.ai/pangolinfo/pangolinfo-amazon-scraper)

## License

MIT
