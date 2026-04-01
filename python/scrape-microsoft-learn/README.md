# Microsoft Learn Scraper

**Author:** Matthew Gonzalez
**Version:** 1.0.0
**Date:** 31-03-2025
**License:** MIT
**Website:** [mgntechvault.com](https://mgntechvault.com)

Download Microsoft Learn training paths and convert them to Markdown, DOCX, or TXT files.

Intended for personal offline study using AI tools such as **Microsoft Copilot Notebook** and **Google NotebookLM** — export your learning paths and feed them directly to your AI notebook for smarter studying.

> **Note:** This tool is not intended to stress or flood Microsoft Learn (DDoS). Use it responsibly and only for your own study materials.

## Requirements

```bash
pip install playwright pyyaml python-docx
playwright install chromium
```

## Usage

Basic usage — choose format interactively:
```bash
python scrape_all_v2.py
```

Specify format directly:
```bash
python scrape_all_v2.py --format markdown
python scrape_all_v2.py --format docx
python scrape_all_v2.py --format txt
```

## Configuration

Edit `config.yaml` to set:
- `paths`: List of Microsoft Learn URLs to scrape
- `output`: Output filename (extension added automatically)
- `title`: Document title

Override via command line:
```bash
python scrape_all_v2.py --format markdown --output MyFile --config custom.yaml
python scrape_all_v2.py --format docx --urls URL1 URL2 URL3
```

## Options

- `--format` — Output format: markdown, docx, or txt (required)
- `--config` — Path to config file (default: config.yaml)
- `--urls` — Override URLs from command line
- `--output` — Output filename without extension
- `--title` — Document title
- `--headed` — Show browser window (for debugging)
- `-v, --verbose` — Verbose logging

## Output

The script generates:
- A single document with table of contents
- All modules and units organized hierarchically
- Timestamps and source URLs
- Log file: `scraper.log`

Supported formats preserve structure and content from Microsoft Learn.

## Notes

- Respects page load times and cookie banners
- Skips navigation elements and assessments
- Retries failed URLs with exponential backoff
- Writes atomically to prevent incomplete files
