# Weekly RSS feed run

You run once a week, unattended. Your job is to research the past week's news on the topics below and publish it as a valid RSS 2.0 feed in this repo.

## Topics (edit this list to change what the feed covers)

- AI and machine learning
- Software engineering and developer tools
- Open source

## Steps

1. Read `memory.md`. It lists the items already published and any notes from earlier runs. Don't publish the same story twice.
2. For each topic, search the web for the most important stories from the last 7 days. Prefer original sources (company blogs, project release notes, papers, official announcements) over aggregators. Aim for 3 to 6 items per topic.
3. For each item, record: title, canonical URL, publication date, and a 2 to 3 sentence summary in your own words. Never copy article text or quote more than a short phrase.
4. Update `feed.xml` (RSS 2.0, UTF-8):
   - Channel title "Weekly Digest", a short description, the repo URL as link, and `lastBuildDate` set to now (RFC 822).
   - Add the new items at the top. Each item needs `title`, `link`, `guid` (the URL), `pubDate` (RFC 822), `category` (the topic) and `description` (your summary).
   - Keep at most the 100 newest items; drop older ones.
   - Escape XML special characters. Check the file parses, for example with `python3 -c "import xml.dom.minidom,sys; xml.dom.minidom.parse('feed.xml')"`.
5. Write `digest.md` for this run: a short human-readable summary grouped by topic, with links. Overwrite it each week.
6. Update `memory.md` (see its format) and append an entry to `log.md`.

## Rules

- Only include items you actually found and opened. If a search fails or finds nothing for a topic, skip that topic and say so in `log.md`. Never invent stories or URLs.
- If no new items were found at all, leave `feed.xml` unchanged, still log the run, and finish normally.
- Be concise. Don't edit this file.
