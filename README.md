# report-schema

The JSON Schema for the opsen report: what an organisation pays for GitHub seats, Copilot, Actions and coding agents, and what it pays for and does not use.

Every report is served at a stable URL:

```
https://opsen.dev/r/<token>.json
```

Create a read-only link in **opsen → Settings → Read-only links**. The token is the secret; revoke it at any time.

## Validate

```bash
pip install check-jsonschema
curl -s "https://opsen.dev/r/$OPSEN_SHARE_TOKEN.json" > report.json
check-jsonschema --schemafile schema/report.schema.json report.json
```

`examples/report.example.json` is a full report for northwind, the example organisation in the [live demo](https://opsen.dev/demo).

## Conventions

- Money is US dollars, as numbers. Timestamps are Unix seconds, UTC.
- `monthly_waste` is the sum of every finding's `monthly_usd`.
- Every finding carries `basis`: the price and the rule behind its figure.
- New fields are added; existing fields are not renamed or removed.

Reference: [opsen.dev/docs/report-json](https://opsen.dev/docs/report-json)
