# Contributing to StoreTalk Help

## How to add or update an article

Each article is a single MDX file. Edit the file directly — standard Markdown works,
plus the Mintlify components below for callouts and steps.

### File locations

| Section | Folder |
|---------|--------|
| Getting Started | `getting-started/` |
| Knowledge Base | `knowledge-base/` |
| AI Staff | `ai-staff/` |
| Inbox | `inbox/` |
| Contacts & CRM | `contacts/` |
| Sales Pipeline | `pipeline/` |
| Campaigns | `campaigns/` |
| Team & Roles | `team/` |
| Billing | `billing/` |
| Consultant Guide | `consultants/` |

### Article frontmatter

Every MDX file must start with:

```mdx
---
title: "Article title"
description: "One-line summary shown in search results."
---
```

### Mintlify components

```mdx
<Tip>Green tip box — use for helpful shortcuts.</Tip>

<Warning>Yellow warning box — use for things that can't be undone.</Warning>

<Note>Blue info box — use for neutral context.</Note>

<Steps>
  <Step title="Step one">Content</Step>
  <Step title="Step two">Content</Step>
</Steps>

<CardGroup cols={2}>
  <Card title="Do" icon="check" color="#1a7f5a">- Item</Card>
  <Card title="Don't" icon="xmark" color="#e8294a">- Item</Card>
</CardGroup>
```

### Adding a new article

1. Create the MDX file in the right folder
2. Add it to the `navigation` array in `mint.json` under the correct group
3. Commit and push
4. Trigger a manual deploy in the Mintlify dashboard (until auto-deploy webhook is configured)

### Adding a new section

1. Create a new folder
2. Add MDX files inside it
3. Add a new `{ "group": "...", "pages": [...] }` entry in `mint.json`

## Logos and favicon

Logos are hosted on Cloudflare R2 at `media.storetalk.app/help/` — do NOT edit via
the Mintlify dashboard logo uploader (it will break). To update logos:

```bash
npx wrangler r2 object put storetalk-media/help/storetalk-light.svg \
  --file logo/storetalk-light.svg --content-type "image/svg+xml" --remote

npx wrangler r2 object put storetalk-media/help/storetalk-dark.svg \
  --file logo/storetalk-dark.svg --content-type "image/svg+xml" --remote
```
