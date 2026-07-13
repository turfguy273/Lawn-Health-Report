# Lawn Health Reports

Turning trouble-spot photos into a texted lawn health report link for Advanced Turf Care customers.

## Where things stand

1. **Report design** — approved. See `templates/report-design-mockup.html` (open in a browser to view).
2. **Issue playbook** — first draft written, wording still needs a pass. This is the "what it means" / "what we'll do" text for each common issue (overwatering, underwatering, shade, crepe myrtle bark scale, whitefly, Pythium blight, mowed too short).
3. **Live report page** — `docs/report.html`. One page that displays any customer's report, filled in from its own link (name, address, photo, and which issue was picked all ride along as part of the URL). This is what the text message links to. The issue wording lives in a `PLAYBOOK` object at the bottom of that file — edit it there any time, no other file needs to change.
4. **Email template** (earlier direction, kept for reference) — `templates/email-template.html`, built as real email-safe HTML.

## The plan (current)

- Technicians already photograph every job in Service Autopilot and pick the issue from a custom dropdown field.
- Service Autopilot can't change its automated message based on that dropdown by itself.
- So a **Zapier automation** sits in between: it watches for "job completed" in Service Autopilot, reads the customer's name/address/photo and which issue was picked, builds a link to `docs/report.html` with that info baked into the URL, and sends that link as a text through **EveryChat**.
- The report page itself decides what wording to show based on the issue in the link — so the Zap stays simple (build a link, send a text), and updating wording later just means editing `docs/report.html`, not touching Zapier.

## Still to do

- [ ] Turn on GitHub Pages for this repo so `docs/report.html` is reachable by a public link (one-time setting, see below)
- [ ] Reword the issue playbook text inside `docs/report.html` (owner's pass)
- [ ] Build the Zapier automation (Service Autopilot → build link → text via EveryChat)
- [ ] Test on one real completed job before trusting it fully

## Turning on GitHub Pages (one-time, ~30 seconds)

1. Open this repo on github.com
2. Go to **Settings → Pages**
3. Under "Build and deployment," set **Source** to "Deploy from a branch"
4. Set **Branch** to `claude/lawn-health-reports-d5dbkm` (or `main`, once this is merged) and folder to `/docs`
5. Save — GitHub will show you the live URL (something like `https://turfguy273.github.io/Lawn-Health-Report/report.html`)

Example link once Pages is on:
`https://turfguy273.github.io/Lawn-Health-Report/report.html?name=Jennifer+Malone&address=412+Whitmore+Trail&date=July+10%2C+2026&area=Back+yard&tech=Marcus+T.&issue=pythium&photo=https%3A%2F%2Fexample.com%2Fphoto.jpg`
