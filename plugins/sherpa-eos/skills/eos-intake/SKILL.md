---
name: eos-intake
version: 0.5.0
description: Stand up an owner's EOS foundation in Strety and populate it. The setup half of the pair; eos-operator runs it day to day. Use whenever a user is starting EOS, wants to build their first quarterly Rocks, start a Scorecard, map their Accountability Chart, or capture their V/TO inputs. Trigger on "set up my EOS," "build my rocks," "start my scorecard," "stand up Strety." Resolves the user at runtime, so it works for any connected user. Shareable across a cohort. On a full Sherpa install it runs after setup-orchestrator + build-owner-profile and reads the owner profile (CLAUDE.md); installed standalone it runs self-contained.
---

# EOS Intake

Stand up the owner's EOS foundation and populate Strety. One focused build, re-run only at annual reset. eos-operator runs it day to day. This skill does not teach EOS or reproduce EOS Worldwide's curriculum or workbooks.

## Built to be shared: resolve identity at runtime

Never hard-code a person, team, or workspace ID. On the first run:
1. Call `get_my_profile` to get the user's person ID, teams, and projects. Use those, whoever they are.
2. **Determine whether the user OWNS the Strety org or is a MEMBER of a shared / cohort org.** Use `get_my_profile` + `get_company`. **Infer ownership from org size and structure, not from the Strety role** — a large `get_company` (many teams / many people) where the user leads only a pod or team means *member of a shared org*, **even if their role shows Admin**. When unsure, ask plainly: "Is this your own Strety company, or a shared / cohort account you're a member of?"
   - **Owns the org**: owner layer = their Leadership team; the V/TO can live natively in Strety.
   - **Member of a shared / cohort org** (e.g. an Owners Club-style instance — they lead a team but don't own the company): the formal Strety **company V/TO is read-only and not theirs to write — never touch it.** Their Rocks, Scorecard, and Accountability Chart still go in **their own team space(s)**, which they can edit. **Ask once where their V/TO should live (Notion, Airtable, a Google Doc, or a Strety team Doc), PIN that location into the owner profile / state file, confirm it back to the user, and note when to revisit (when they own their own Strety org).** Do not silently default to a hidden state file.
3. Before interviewing, read any V/TO or state that already exists in that store and pre-fill from it. Never re-ask a field that is already answered.
4. If the user runs operations in ClickUp or another task system, get the workspace ID once and store it. Do not assume it.

## Operating principle

Pull first, interview only for gaps. Do not ask anything already in memory, the project, or a connected source. Show pre-filled drafts; the user edits and approves. Never start from a blank field.

**Read the owner profile first.** If a `CLAUDE.md` Owner Profile (or any normal account / working memory) is present, harvest it before anything else. On a full Sherpa install, build-owner-profile has already run, so most of the vision and structure is there; installed standalone there may be only ordinary `CLAUDE.md` account memory — pull whatever exists and interview the rest. Sequencing on a full install is owned by setup-orchestrator (it builds the profile first, then calls this); installed alone, just run.

## Order of build

1. Resolve identity and the owner layer (above).
2. Accountability Chart = the seats the owner currently wears, which doubles as the Automate then Delegate then Eliminate map.
3. Quarterly Rocks, one owner each, tagged CONTROL or MONEY or KILL, due end of the coming quarter.
4. Scorecard rows and weekly goals. Start lean (3 to 7) and grow toward 5 to 15 as numbers earn their place.
5. Collect V/TO inputs (see handoff below) into the state file. The Operator places and maintains the V/TO.
6. Write Rocks and metrics to Strety over MCP; record everything in the state file.

## Step 1: Pull what exists

**Start with `CLAUDE.md` (the owner profile / account memory), then the project and connected sources.** Map each profile section to its V/TO field so you never re-ask what's known:

| From CLAUDE.md | Seeds EOS field | Then |
|---|---|---|
| `## Mount Everest` + install goal | Core Focus / 10-year target | confirm, don't re-ask |
| `## My world…` → Team / who-owns-what | Accountability Chart seats | confirm + extend to formal seats |
| `## …Entities` + Source map | entity structure / which org + workspace | reuse |
| `## Who I am` (Rocket Fuel / strengths / blind spots) | how to run the owner L10 + GWC framing | inform tone |

Map current projects to Rock candidates and open threads to Issues. Draft what you can. Present it. If no profile exists (standalone install with only normal account memory), pull whatever `CLAUDE.md` holds and treat the rest as gaps for Step 2.

## Step 2: Interview only for the gaps

Ask only for EOS fields not known and not inferable:
1. 10-year target (if Mount Everest was harvested in Step 1, confirm/refine rather than ask cold).
2. 3-year picture.
3. 1-year plan (revenue, profit, goals).
4. This quarter's Rocks (3 to 7), each with a clear done condition.
5. Scorecard metrics and weekly goals.
6. Confirm core values (edit if they have drifted).
7. Marketing strategy per company (target market, three uniques, proven process, guarantee).

One question at a time when it needs thought; batch the quick confirmations. Front-load the judgment calls (values, which Rocks matter), back-load the mechanical entry.

## Step 3: Solo-operator adaptations

If the user runs without a leadership team:
1. The Accountability Chart is the seats they wear; build it carefully, it is the most useful artifact.
2. People Analyzer parks until a hire.
3. Run GWC on the user per seat to surface what to offload first.
4. The owner L10 is their weekly solo discipline meeting.

## Step 4: Write to Strety (MCP)

Write Rocks and metrics directly over the Strety MCP. Batch the create calls in one block. Terminal or destructive actions (cancel or complete a rock) need an in-UI approval tap, so flag those instead of retrying. Report any failure plainly, never fake a write. A boolean metric (e.g. "did the L10 happen") is a number metric with target_type 'eq' and target_value 1. Mirror state to the state file.

## V/TO handoff

Collect the V/TO content during the interview and store it in the **pinned V/TO store** chosen at identity resolution — for a shared-org user that is Notion / a Doc, **never** the read-only Strety company V/TO — and mirror it to the state file. Record the store location in the owner profile so eos-operator and future runs reuse it without re-asking. The Operator maintains it. **Tell the user where the V/TO lives.**

## Definition of done

The user's **team space(s)** hold the Accountability Chart (seats), a lean Scorecard with weekly goals, and this quarter's Rocks with owners and CONTROL/MONEY tags. V/TO inputs live in the pinned store (and mirror to the state file) for the Operator. No field left as a silent blank; mark unknowns as draft placeholders.

**Close every run by telling the user exactly where each artifact landed** — which Strety team space holds the Rocks and Scorecard, and which store (Notion page / Doc / state file) holds the V/TO. Never let the user believe something was "filled in" when it only went to a file they can't see. Then hand off to the Operator.

## Guardrail

Templates and field lists are a neutral way to organize the user's own business data. Never paste EOS Worldwide's copyrighted worksheet or workbook text into any shipped file.

## Changelog

- 0.5.0 — Hardened the shared-org case: ownership is inferred from org size/structure not the Strety role (Admin in a 200+ person cohort is still a member, not an owner); the V/TO store is pinned to the owner profile and confirmed to the user; every run ends by reporting exactly where each artifact was written. Never writes a read-only shared company V/TO.

- 0.4.0 — Profile-aware: reads the owner profile (CLAUDE.md) first and maps Mount Everest / team / entities into V/TO seeds; runs after setup-orchestrator + build-owner-profile on a full install, self-contained standalone. Asks only the EOS-specific gaps.

- 0.3.0 — Templatized for any connected user (runtime identity via `get_my_profile`, no hard-coded IDs). Added company-vs-team detection with a conditional database choice for team-level users. Reads existing V/TO and state before interviewing. V/TO placement handed to eos-operator.
- 0.2.0 — Switched writes to the Strety MCP (dropped browser and paste-block paths). Owner layer placed in the person space inside shared orgs. Boolean metric defined as a number with an equals-1 goal.
- 0.1.0 — Initial build: Rocks, Scorecard, Accountability Chart, V/TO interview.
