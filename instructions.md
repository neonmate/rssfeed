# Weekly RSS feed run

You run once a week, unattended. Your job is to research the past week's news on the topics below and publish it as a valid RSS 2.0 feed in this repo.

## Topics (edit this list to change what the feed covers)

- AI and machine learning
- Software engineering and developer tools
- Open source

## Source feeds

- Augsburger Allgemeine, Augsburg section: http://www.augsburger-allgemeine.de/augsburg/rss (topic: "Augsburg")

Read each source feed with WebFetch and add its newest items from the last 7 days under the given topic. If a source is blocked or unreachable, don't work around it with curl or mirrors: log the error in `log.md`, add a note to `memory.md` and carry on without it.

## Filtering (applies to every item, especially the Augsburger Allgemeine feed)

- **Deduplicate by story, not by headline.** If several items cover the same story or ongoing topic with different headlines (for example three articles about one closed swimming pool: "stays closed", "how the swim team copes", "reopening takes longer"), keep only one: the most informative, most recent or most factual one. Compare against the items already in `feed.xml` and `memory.md` too, so a follow-up article on a story published in an earlier week is skipped unless it contains a genuinely new development (a decision, an opening date, a result). In that case, mention in the summary that it updates the earlier story.
- **Drop clickbait:** teaser or question headlines that withhold the point ("Das passiert jetzt…", "Darum…", "So reagiert…"), listicles ("Die zehn besten…"), and pure engagement bait.
- **Drop police reports** (Polizeibericht, Unfälle, Einbrüche, Diebstähle, Festnahmen, Verkehrskontrollen, Feuerwehreinsätze and similar blotter items), unless it is a major event with real public significance and is reported factually.
- **Drop sensational reporting:** crime and accident drama, celebrity gossip, outrage pieces, speculation and horoscope-style content. Prefer sober, fact-based reporting such as local politics, city decisions, business, infrastructure, education, culture events and science.
- When in doubt whether an item is clickbait or sensational, leave it out. Fewer, better items are preferred over filling the quota.
- In `log.md`, record how many items were dropped per rule (duplicate, clickbait, police, sensational), without listing every headline.

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
