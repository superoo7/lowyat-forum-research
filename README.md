# Lowyat Forum Research Tool

A Claude Code skill that lets you research any topic on [Lowyat forum](https://forum.lowyat.net) — Malaysia's largest online community. It searches for relevant threads, scrapes them into Excel files, and analyzes the results.

## How It Works

```
User Question → Search Forum → Scrape Threads → Analyze & Summarize
```

1. **Search** — Finds relevant Lowyat forum threads using web search with multiple keyword angles
2. **Scrape** — Crawls selected threads and saves every post to `.xlsx` files (Name, Date, Comment)
3. **Analyze** — Reads the scraped data and synthesizes findings into a structured summary

## Installation

### As a Claude Code Skill

Copy the skill folder into your project:

```bash
cp -r .claude/skills/lowyat-scraper <your-project>/.claude/skills/
cp datascraping.py <your-project>/
cp pyproject.toml <your-project>/
```

Then install dependencies:

```bash
cd <your-project>
uv sync
```

### From ClawHub

Install from [clawhub.ai/superoo7/lowyat-forum-research](https://clawhub.ai/superoo7/lowyat-forum-research).

### Manual Setup

```bash
git clone https://github.com/johnson/datascraping-lowyat.git
cd datascraping-lowyat
uv sync
```

## Usage

### With Claude Code (Skill)

Just ask Claude to research a topic:

```
> I want to research water heaters on Lowyat forum
> What do Lowyat users say about Toto toilets?
> Research mechanical keyboards on LYN
```

Claude will automatically search, scrape, and analyze.

### Standalone Scraper

```bash
uv run python datascraping.py https://forum.lowyat.net/topic/5411252
```

Output: `5411252.xlsx` with columns `Name`, `Date`, `Comment`.

## Scraper Details

- Auto-detects total pages and crawls all of them
- 20 posts per page, paginated via `/+N` URL suffix
- Random 0.5–2s delay between requests (respectful scraping)
- Saves incrementally after each page — safe to interrupt and resume
- If the `.xlsx` file already exists, appends to it

## Example Output

| Name | Date | Comment |
|------|------|---------|
| forumer123 | 15-3-2025, 10:30 AM | I recommend Johnson Suisse for budget... |
| prouser456 | 15-3-2025, 11:45 AM | Toto is the gold standard but pricey... |

## Tech Stack

- Python 3
- [requests](https://docs.python-requests.org/) — HTTP requests
- [BeautifulSoup4](https://www.crummy.com/software/BeautifulSoup/) + html5lib — HTML parsing
- [openpyxl](https://openpyxl.readthedocs.io/) — Excel output
- [tqdm](https://tqdm.github.io/) — Progress bars
- [uv](https://docs.astral.sh/uv/) — Package management

## Links

- **ClawHub**: [clawhub.ai/superoo7/lowyat-forum-research](https://clawhub.ai/superoo7/lowyat-forum-research)
- **GitHub**: [github.com/superoo7/lowyat-forum-research](https://github.com/superoo7/lowyat-forum-research)

## ClawHub Metadata

| Field | Value |
|-------|-------|
| Slug | `lowyat-forum-research` |
| Display Name | Lowyat Forum Research & Analysis |
| Owner | johnson |
| Version | 1.0.0 |
| Tags | `lowyat`, `forum`, `malaysia`, `research`, `analysis`, `consumer-review`, `web-scraping`, `data-extraction` |

## Attribution

Forked from [KennethLeeJE8/datascraping-lowyat](https://github.com/KennethLeeJE8/datascraping-lowyat).

## License

[MIT](LICENSE)
