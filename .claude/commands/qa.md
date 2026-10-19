---
description: Delegate to the qa subagent for test planning, bug hunting, and verification. Pass multiple items (e.g. "US1, US2, US3") to run them in parallel.
---

Parse $ARGUMENTS into one or more distinct items to test (e.g. separate
user stories, tickets, or features — split on commas, "y"/"and", or
newlines; if it's a single request, treat it as one item).

- **One item:** invoke the `qa` subagent (Agent tool, subagent_type:
  "qa") once, with full context on the feature/change in question,
  including relevant file paths, acceptance criteria, and scope
  boundaries.
- **Multiple items:** invoke the `qa` subagent once per item, **in
  parallel** — all Agent tool calls in the same response/message, never
  sequentially. Each call's prompt must be fully self-contained (the
  subagent has no shared context): identify the specific item by name,
  give its acceptance criteria/description if known or ask the user to
  look it up, point to the relevant files/paths, and state explicitly
  that it should only test that item, not the others running in
  parallel.

After launching, report back which items are running and that their
reports will come back as separate findings to synthesize once all
complete.

Request: $ARGUMENTS
