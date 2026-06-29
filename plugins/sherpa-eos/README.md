# Sherpa EOS

Run your EOS (Entrepreneurial Operating System) on Claude. `sherpa-eos` stands up your EOS foundation and runs the weekly cadence — built for [Cowork](https://claude.com/product/cowork), also works in Claude Code. It ships as **two skills that work as a pair**:

- **eos-intake** — the setup half. Builds the foundation: Accountability Chart (the seats you wear), this quarter's Rocks, a lean Scorecard, and your V/TO inputs.
- **eos-operator** — the run half. Runs the weekly cadence: Level 10 (L10) prep, Scorecard check-ins, Rock updates, IDS on issues, and V/TO placement/upkeep.

This module organizes *your own* business data into the EOS structure. It does **not** teach EOS or reproduce EOS Worldwide's copyrighted worksheets, workbooks, or curriculum.

## Two ways to run it

**Standalone (just EOS on your Claude).** Install this plugin on its own and run `/eos-intake`. It harvests whatever's already in your `CLAUDE.md` / account memory, pre-fills what it can, and asks only the gaps — then `eos-operator` runs your week. No other Sherpa plugin required.

**As part of the full Sherpa OS.** If you also run `sherpa-core`, `setup-orchestrator` builds your **owner profile first**, and `eos-intake` reads it — pulling your Mount Everest → Core Focus / 10-year target, your team / who-owns-what → Accountability Chart seats, and your entity structure straight from the profile, so you're never re-interviewed. You only answer the EOS-specific questions (core values, marketing strategy, 3-year / 1-year, Rocks, Scorecard).

Same skill, both paths — it adapts to what's installed.

## Installation

### Cowork

Add the Sherpa OS marketplace via **Customize → Plugins → Add marketplace**, then install **sherpa-eos**.

### Claude Code

```bash
claude plugin marketplace add SherpaOS/sherpa-os-marketplace
claude plugin install sherpa-eos@sherpa-os
```

## First run

Run **`/eos-intake`**. It will:

1. Resolve who you are at runtime and whether you sit at the **company** level (your V/TO lives natively) or **team** level (it asks once where the V/TO/state should live).
2. Pull what already exists — `CLAUDE.md` / account memory first, then your project and any connected sources — and present pre-filled drafts.
3. Interview only the gaps, one judgment call at a time.
4. Write Rocks and Scorecard metrics, and hand the weekly cadence to `eos-operator`.

Then, day to day, just say things like **"run my L10," "check in my scorecard," "how are my rocks," "update my V/TO," or "what do I owe this week"** — that's `eos-operator`.

## Strety (optional data backend)

`sherpa-eos` works with or without [Strety](https://strety.com):

- **Strety connected** → Rocks, Scorecard, and L10 state read/write live in Strety over its connector.
- **No Strety** → EOS still runs as your framework and coaching layer; the V/TO and state live in the store `eos-intake` picks with you (Notion, Airtable, a Google Doc, or a Strety Doc).

EOS runs either way — Strety just adds the live data layer.

## What's in the box

| Skill | What it does | Just say… |
|---|---|---|
| **eos-intake** | Stand up the EOS foundation — Accountability Chart, Rocks, Scorecard, V/TO inputs. One focused build; re-run at annual reset. | `/eos-intake`, "build my rocks", "start my scorecard", "stand up Strety" |
| **eos-operator** | Run the weekly cadence — L10 prep, Scorecard check-ins, Rock status, IDS, V/TO upkeep. | "run my L10", "check in my scorecard", "how are my rocks", "what do I owe this week" |

## Part of Sherpa OS

`sherpa-eos` is one module of the **Sherpa OS** owner-operating-system. Run it alone for EOS, or add `sherpa-core` (onboarding + owner profile) and `sherpa-owner` (the cross-entity Owner Daily Brief) for the full stack. — Sherpa HQ / Jamie White · https://s4o.ai
