# Reviewer guide and reproducible checks

[한국어](reviewer-guide.ko.md)

## Scope and capabilities

Podium is a readable instruction/template bundle, not an orchestration service. The host model and tools perform operations. No Podium account, backend, MCP server, hook, or package launcher is required. Reviewers use their own host account and a disposable workspace containing fictional data; do not share personal credentials.

| Capability | Required host support | Without it |
|---|---|---|
| File-based setup, status, rule comparison | Read/write access to the selected project and user approval for edits | Explain the missing access and provide the proposed files/patch; do not claim files were changed |
| Session search | An actual session search/read tool | Search project records only and identify the limitation |
| Session creation, placement, archiving | Actual host session/sidebar tools and approval for the specific operation | Provide the brief and manual steps; do not invent session IDs or placement |
| Work handover | Persistent workspace files; optional session tools | Prepare a file-based brief for the user to open manually |

The directory may classify a skills-only bundle for Claude Code, Cowork, and Claude apps. That classification is not evidence that every surface exposes the session tools or has passed a live workflow test. Claude Code CLI installation/update integrity was verified through v0.2.3. Historical desktop workflow observations and their limits are in [design notes](design-notes.md). Current full-flow tests on Cowork, web, and mobile remain unverified.

## Three reproducible scenarios

Use the installed version shown by its manifest. Record host/CLI version, model, available tools, date, exact prompts, user answers, and before/after workspace files. Installation checks do not replace these behavioral tests. Expected results below are test criteria, not claims of completed execution.

1. **Setup and approval.** In an empty disposable project ask: “Set up podium for this empty project. Only prepare the project files; do not create or move sessions.” It should propose a file plan and wait. Declining should leave files unchanged. In a separate approved run it should create only the approved project files. Repeat setup: it should detect the installation without duplicating rules or resetting task records.
2. **Read-only status.** Copy the fictional [notification example](../examples/dev-notification/README.md) to a disposable project and mark one step done and another blocked. Ask: “Using this fictional workstream record, tell me what is done, what is blocked, and what comes next. Do not edit anything.” It should cite the supplied records, distinguish unknown runtime state, and leave every project file unchanged.
3. **Rule comparison and rejection.** Prepare a fictional project with a custom ledger path, task data, unrelated project rules, and an old bounded Podium section. Ask: “Compare this project's podium rules with the installed version and show a patch. Do not apply it or update the plugin.” It should preserve custom context, show a bounded patch or ask about an ambiguous boundary, and wait. Answer “Leave unchanged”: no files or installed plugin should change. A separate approved-patch run can test narrow application and rollback.

Use hashes/diffs to verify writes and non-writes. Save model output separately from the fixture. Inspect tool calls to distinguish a proposed action, an attempted action, and verified completion. If the model fails, record the failure and version rather than rewriting the evidence as a pass.

## Troubleshooting and review notes

- Missing session tools are a host capability limit. Use manual handoff; installing this bundle does not add those tools.
- Updates replace the plugin, not project records. Project rule migration needs a separately approved patch; see [updating](updating.md).
- Private data can appear in project files or conversation excerpts. See [privacy](privacy.md); a local file is not a guarantee of local-only host processing.
- The directory flagged download-and-run patterns in the icon and banner PNGs in v0.2.3. Those files are image assets; the bundle declares no execution component. PNG structure/CRC checks passed. This suggests a binary-content match but is not an official false-positive determination. Keep review findings visible and respond with file/version evidence if requested.
- The v0.2.3 data-only tag excludes developer scripts, repository automation, and the marketplace catalog. Those remain on `main`. Approval and publication are separate from installation and security scan results.
- Report general issues through GitHub Issues; use [SECURITY.md](../SECURITY.md) for private vulnerability reports.
