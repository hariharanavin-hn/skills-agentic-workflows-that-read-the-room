---
name: update-github-info
description: Draft reviewed website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
    - awesome-copilot.github.com
engine:
  id: copilot
  copilot-sdk: true
---

# Update Mona's GitHub Info website

## Purpose

Review recent official GitHub announcements and identify concise, practical updates that help developers learn GitHub faster. Prepare the proposed changes for Mona's human review. Do not publish or merge changes.

## Required sources

1. Read `notes/mona-notes.md` and follow Mona's writing and review requirements.
2. Fetch and review `https://github.blog/latest/` for recent GitHub Blog information.
3. Fetch and review `https://github.blog/changelog/` for recent GitHub Changelog information.
4. Fetch and review `https://awesome-copilot.github.com/workflows/` for relevant workflow patterns or examples that may improve Mona's GitHub Info updates.

Use repository guidance and source material through GitHub repository API tools. Use web fetch for external public guidance. Do not use terminal, CLI, or sandboxed commands to inspect repository guidance or external sources.

## Permitted changes

Modify only `site/content/github-info.md`. Do not modify workflow files, repository configuration, tests, assets, or other site files. Preserve the existing document structure and writing style unless a source clearly warrants a direct change.

## Proposed update format

Add only information that is relevant to Mona's audience and supported by a consulted source. Keep summaries short and practical. When a change comes from the GitHub Blog or GitHub Changelog, include a Markdown source link and identify the source clearly.

For each update, include:
- a concise, user-facing summary;
- why it is relevant to developers using GitHub; and
- a direct source link.

## Pull request review

Create one draft pull request using `safe-outputs` with `create-pull-request`. Rely on `safe-outputs` for the branch and pull request; do not write directly to `main` or bypass the pull request workflow.

Use a pull request title that mentions Mona or GitHub Info. In the pull request body, include:
- a brief summary of the proposed website changes;
- the Mona notes applied;
- the GitHub Blog and GitHub Changelog items consulted, with links;
- any Awesome Copilot workflows patterns consulted, with links;
- the exact files changed; and
- a short review checklist stating that the change is limited to `site/content/github-info.md`, source links are present, and no unsupported claims were added.

## Review guardrails

Stop and produce no changes if the sources cannot be read or no relevant update can be identified. Do not invent dates, features, claims, or source context. Keep the pull request suitable for a human to review before merging.
