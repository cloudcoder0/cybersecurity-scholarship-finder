# cybersecurity-scholarship-finder

Automated MVP CLI tool to discover cybersecurity scholarships and grants from **50+ non-traditional sources** (government agencies, nonprofits, libraries, associations, conferences, companies, and academic centers), while enforcing robots.txt checks before crawling.

## Features
- Robots.txt-aware crawling (skips pages when disallowed/unavailable).
- Source catalog of 50+ niche sources (avoids traditional scholarship aggregator sites).
- Dynamic source discovery from web search queries (`discover` command) so your source pool grows over time.
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
./main discover --query "cybersecurity scholarship grant for women veterans first-generation"
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
- If `robots.txt` is missing (HTTP 404), crawl is allowed by default; if robots cannot be verified due to network/parsing issues, source is skipped.
- Data extraction is heuristic and should be reviewed before applying.
