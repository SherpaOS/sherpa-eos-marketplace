# Sherpa EOS — Public Marketplace

Run your EOS (Entrepreneurial Operating System) on Claude. `sherpa-eos` stands up your EOS foundation and runs the weekly cadence as two paired skills: **eos-intake** (build Rocks, Scorecard, Accountability Chart, V/TO) and **eos-operator** (weekly L10, check-ins, IDS).

## Install

In Claude Code / Cowork:

```
/plugin marketplace add SherpaOS/sherpa-eos-marketplace
/plugin install sherpa-eos@sherpa-eos
```

## Requirements

- Runs against the **Strety** MCP connector (optional data backend). Connect Strety to read/write Rocks, Scorecard, and L10 state live. Without it, EOS still runs as your framework and the V/TO lives in a store you choose. See `plugins/sherpa-eos/CONNECTORS.md`.

## Updates

```
/plugin marketplace update sherpa-eos
```

---

> **Note:** This public repo is an automatic **mirror**. The source of truth for `sherpa-eos` is the private Sherpa OS marketplace; changes there sync here. Open issues here, but PRs to plugin files may be overwritten by the next sync.

— Sherpa HQ / Jamie White · https://s4o.ai
