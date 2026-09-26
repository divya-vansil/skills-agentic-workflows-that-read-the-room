---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  edit:
  web-fetch:

network:
  allowed:
    - defaults
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[GitHub Info] "
    reviewers: [mona]
    draft: true
---

# Update GitHub Info

Keep `site/content/github-info.md` current with useful, recent GitHub guidance for developers.

## Instructions

1. Read `notes/mona-notes.md` and the current `site/content/github-info.md` before making decisions.
2. Use the `web-fetch` tool to read both `https://github.blog/latest/` and `https://github.blog/changelog/` on every run. Follow relevant links on those official pages when needed to verify details.
3. Select only recent updates that are useful for developers learning GitHub. Keep summaries short and practical, avoid repeating existing content, and do not infer facts that the sources do not support.
4. Update only `site/content/github-info.md`. Keep its existing Markdown structure and editorial angle unless a small structural change is necessary. Attribute each new or changed item to its GitHub Blog or Changelog source with a direct link.
5. If there is no meaningful update, make no changes and do not open a pull request.
6. When the file has meaningful changes, create one draft pull request using the configured `create-pull-request` safe output. Summarize the changes and link their sources in the pull request body, and ask Mona to review it. Do not push changes or write directly to the default branch.