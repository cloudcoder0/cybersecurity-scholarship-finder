## ABSTRACT: 
This is a CLI-based web scraper that combines dynamic scraping with 50+ hard coded sources to parse and return cybersecurity based scholarships to the user. It's designed to be used in a Linux environment. This project allows you to set and create a profile based on name, GPA, and state to find scholarships where you meet the requirements. The dynamic web scraper works by utilizing the discover argument to run a search query for whatever you want to expand your potential pool of scholarships, and the crawl argument scrapes potential scholarships from parsed URLs. The discover argument is optional, and if you don't want to use it you can just run crawl to utilize the pre-installed sources. This tool also undergoes legal compliance with robots.txt policies to ensure no illegal activity is being done.

## Usage
```bash
./main sources
./main discover --query "Whatever you want here"
./main crawl --limit-sources 10 (pick whatever number you want)
./main profile set --name "Test" --gpa 3.7 --state CA
./main match --name "Test" --limit 15 --as-of 2026-04-06 (change date to the actual date in this format)
./main latest --limit 10 --as-of 2026-04-06 (change date to the actual date in this format)
./main export --out opportunities.json --as-of 2026-04-06 (change date to the actual date in this format)
./main prune --as-of 2026-04-06 (change date to the actual date in this format)
```

## Interactive mode
Run with no arguments:
```bash
./main
```

## Notes
- Some sites may block bots, require JS rendering, or have strict robots rules.
- If `robots.txt` is missing (HTTP 404), crawl is allowed by default; if robots cannot be verified due to network/parsing issues, source is skipped.
- Expired scholarships are automatically removed after crawl and are filtered out of `latest`, `match`, and `export` using today (or a provided `--as-of YYYY-MM-DD` date).
- Data extraction is heuristic and should be reviewed before applying.
