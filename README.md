# cybersecurity-scholarship-finder

Automated MVP CLI tool to discover cybersecurity scholarships and grants from **50+ non-traditional sources** (government agencies, nonprofits, libraries, associations, conferences, companies, and academic centers), while enforcing robots.txt checks before crawling.

## Features
- Robots.txt-aware crawling (skips pages when disallowed/unavailable).
- Source catalog of 50+ niche sources (avoids traditional scholarship aggregator sites).
- Local SQLite persistence (`scholarships.db`).
- User profiles (`name`, `gpa`, `state`) for matching.
- Matching score engine for eligibility hints.
- Opportunity output includes:
  - short description
  - requirements (best-effort extraction)
  - amount awarded (best-effort extraction)
  - due date (best-effort extraction)
- Interactive ASCII-art CLI menu and command mode.

## Quick start
```bash
./main sources
./main crawl --limit-sources 10
./main profile set --name "Alex" --gpa 3.7 --state CA
./main match --name "Alex" --limit 15
./main latest --limit 10
./main export --out opportunities.json
```

## Interactive mode
Run with no args:
```bash
./main
```

## Notes
- This is an MVP web crawler. Some sites may block bots, require JS rendering, or have strict robots rules.
- If robots.txt cannot be fetched/parsed, the crawler defaults to **skip** for compliance.
- Data extraction is heuristic and should be reviewed before applying.
