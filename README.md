# UVRN — Universal Verification Receipt Network

**UVRN** is an open protocol for producing cryptographically verifiable receipts from multi-source evidence. It measures whether independent sources **agree, disagree, conflict, or show early potential** about a claim — and makes that measurement **provable** to anyone, human or machine.

This repository is the **org directory and protocol home** for [UVRN-org](https://github.com/UVRN-org).

---

## Disclaimer

UVRN is in **Alpha**. The protocol measures the **relationship between your sources** — not whether any source is correct. Final trust of any output rests with the user. Aligns with [uvrn.org](https://www.uvrn.org).

---

## Quickstart

### Validate DRVC3 genesis receipts (local)

```bash
git clone https://github.com/UVRN-org/uvrn.git
cd uvrn
npm install -g ajv-cli
ajv validate -s schemas/drvc3.schema.json -d "receipts/uvrn-receipt-ex1.json"
# or validate all: ajv validate -s schemas/drvc3.schema.json -d "receipts/*.json"
```

### Connect an AI agent (MCP)

```bash
npx -y @uvrn/mcp
```

Full connector recipes: [`uvrn-packages/uvrn-mcp/CONNECT.md`](https://github.com/UVRN-org/uvrn-packages/blob/main/uvrn-mcp/CONNECT.md)

---

## Repositories

| Repo | Role |
|------|------|
| **[uvrn-packages](https://github.com/UVRN-org/uvrn-packages)** | **Implementation monorepo** — 33 `@uvrn/*` packages @ 5.x (Delta Engine, CLI, API, MCP, receipt model) |
| **[uvrn-home](https://github.com/UVRN-org/uvrn-home)** | Public website ([uvrn.org](https://www.uvrn.org)) |
| **[uvrn-worker](https://github.com/UVRN-org/uvrn-worker)** | Optional network ingest worker |

**Previous protocol seed:** Content formerly in `uvrn-base` now lives here. Implementation contracts of record: [`uvrn-packages/SPEC/`](https://github.com/UVRN-org/uvrn-packages/tree/main/SPEC).

---

## npm packages (core six)

| Package | Description |
| -------- | ----------- |
| [@uvrn/core](https://www.npmjs.com/package/@uvrn/core) | Delta Engine core (run, validate, verify) |
| [@uvrn/sdk](https://www.npmjs.com/package/@uvrn/sdk) | TypeScript SDK |
| [@uvrn/cli](https://www.npmjs.com/package/@uvrn/cli) | CLI (bundle → receipt) |
| [@uvrn/api](https://www.npmjs.com/package/@uvrn/api) | REST API server |
| [@uvrn/mcp](https://www.npmjs.com/package/@uvrn/mcp) | MCP server — **13 tools** for AI assistants |
| [@uvrn/adapter](https://www.npmjs.com/package/@uvrn/adapter) | DRVC3 envelope adapter (EIP-191 signing) |

Full **33-package** list: [`uvrn-packages` README](https://github.com/UVRN-org/uvrn-packages#readme).

---

## Protocol evolution

| Generation | Where | Notes |
|------------|-------|-------|
| **DRVC3 genesis** | `schemas/` + `receipts/` in this repo | Base receipt structure; validate with ajv |
| **v5 receipts** | `@uvrn/receipt` + [`SPEC/`](https://github.com/UVRN-org/uvrn-packages/tree/main/SPEC) | NetworkReceipt envelope, signing, measurement semantics |

Existing v3 receipts and `verifyReceipt()` remain byte-for-byte valid (additive-only rule).

---

## MCP tools (13)

`delta_run_engine`, `delta_validate_bundle`, `delta_verify_receipt`, `delta_score_drift`, `delta_compare`, `delta_verify_identity`, `delta_canon_qualify`, `delta_canon_get`, `delta_score_claim`, `delta_read_support`, `delta_report_rank_stability`, `delta_validate_datapoint`, `delta_pattern_scan`

Machine-readable contract: [`uvrn-packages/uvrn-mcp/plugin-manifest.json`](https://github.com/UVRN-org/uvrn-packages/blob/main/uvrn-mcp/plugin-manifest.json)

---

## Schema and examples (this repo)

- **Schema:** [schemas/drvc3.schema.json](schemas/drvc3.schema.json)
- **Examples:** [receipts/uvrn-receipt-ex1.json](receipts/uvrn-receipt-ex1.json), [receipts/uvrn-receipt-minimal.json](receipts/uvrn-receipt-minimal.json)

---

## Principles

- **Protocol-first** — schemas + receipts are canonical seed; v5 contracts live in `uvrn-packages/SPEC/`
- **Replayable** — every receipt can be revalidated anywhere
- **Proof over trust** — verification = receipts, not screenshots
- **Honest vocabulary** — integrity-checked ≠ verified without a valid producer signature

---

## License

MIT
