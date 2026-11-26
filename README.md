# Strategic Accountability Dashboard

A live Cowork dashboard plus a comms skill that help Dan drive accountability and impact across his three GSO Big Rocks, with a focus on stakeholder management.

![Dashboard snapshot](docs/dashboard-snapshot.jpg)

## What it does

| View | Purpose | Source |
|---|---|---|
| Next Best Action | AI-generated highest-impact stakeholder move | `askClaude` over live deals + static context |
| My Actions | 8 personal actions, colour-coded by urgency | Static (from meeting notes) |
| Initiatives (Big Rocks) | Milestone progress for the 3 deliverables | Static |
| Upcoming meetings | Prep notes for the next events (Jul 1 SSC is critical) | Static (from calendar) |
| Deal pipeline | Pending approvals, TCV, tier, due date | **Live** – Asana project `1214802974574972` |
| Stakeholders | Engagement status for 10 key people | Static |
| Comms required | Outstanding messages to send | Static |

### The three Big Rocks
1. **Strategic ABs** – deal agent live, UK terms done; AU, US, approval thresholds, TCO outstanding
2. **MBR (Business Performance)** – June delivered; July pack 80% by Jul 1, dry run Jul 2, MBR Jul 9
3. **Sales Planning CoE** – planning calendar, territory/quota/comp integration, digital transformation

## Repo layout

```
JTBD/
├── README.md
├── dashboard/accountability-dashboard.html   # source of the live artifact
├── skills/
│   ├── accountability-comms.skill            # installable skill (zip)
│   └── accountability-comms-SKILL.md         # readable copy of SKILL.md
└── docs/
    ├── dashboard-snapshot.jpg                # visual snapshot
    └── skill-eval-review.html                # with/without-skill test results
```

The dashboard is published as the Cowork artifact `strategic-accountability-dashboard`. Pulls from Asana on every open.

## Skills required

| Skill / file | Role | Status |
|---|---|---|
| `skills/accountability-comms.skill` | Drafts Slack, email, pre-reads, escalations using Dan's Big Rocks, stakeholders, and meeting context | Built, tested (86.7% vs 60% baseline pass rate) – **install via Settings → Capabilities** |
| `accountability-digest-9am/SKILL.md` | Scheduled task, weekdays 9am AEST: Slack DM digest | Built (in `~/Documents/Claude/Scheduled/`) |
| `accountability-digest-3pm/SKILL.md` | Scheduled task, weekdays 3pm AEST: Slack DM digest | Built (in `~/Documents/Claude/Scheduled/`) |
| Dashboard-update skill | Would update milestones/actions/meetings on request | **Not built** – scoping question was interrupted |

Related skills already installed: `weekly-status-update`, `deal-intake`, `xe-meeting-summary`, `xe-asana-chaser`.

## Connectors used

Asana (deals, my tasks), Slack (#partner_mbr `C08AHP9Q85B`, digests), Google Calendar, Google Drive (Big Rocks deck, Gemini notes). Gmail returned empty results, so email follow-ups are not included.

## Known issues / next steps

- **Dates are hardcoded to 26 Jun 2026.** `TODAY` in the script, the "5 days to SSC" KPI, and the static meetings, actions, and NBA prompt are all stale. Needs a refresh pass, ideally by pulling calendar and actions live.
- Most sections are static; only the deal pipeline and NBA are live.
- Gmail search returned nothing; recheck the connector.
- Build the dashboard-update skill so edits don't require a full rebuild.
- Scheduled-task digests reflect the same static context and need the same refresh.
