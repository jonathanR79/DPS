# DPS Cost Calculator

A static website for estimating yearly **Dynatrace Platform Subscription (DPS)** licence costs based on expected usage.

## Live Site

This folder (`docs/`) is deployed via **GitHub Pages**. Once enabled in your repository settings (Settings → Pages → Source: `docs/`), the site is available at:

```
https://<org>.github.io/dps/
```

## Pages

| Page | Description |
|------|-------------|
| **index.html** | Capability selector — pick the DPS capabilities you want to estimate |
| **calculator.html** | Usage calculator for the main capabilities (Full-Stack, Infrastructure, Foundation & Discovery, Synthetic, RUM) |
| **logs.html** | Capability selector for Log Management & Analytics |
| **logs-calculator.html** | Usage calculator for log capabilities |
| **other.html** | Capability selector for all remaining capabilities (security, traces, events, automation, etc.) |
| **other-calculator.html** | Usage calculator for the remaining capabilities |

## How It Works

1. Select one or more capabilities on the selector page.
2. Enter your expected usage (e.g. number of hosts, GiB of memory, monitors, sessions, etc.).
3. The calculator multiplies usage × unit price × time to give you a projected yearly cost.
4. Copy the summary to your clipboard for easy sharing.

All state is kept in `sessionStorage` — nothing is sent to any server.

## Rate Card

The included `ratecard.json` contains the **public list prices in USD** from the [official Dynatrace pricing rate card](https://www.dynatrace.com/pricing/rate-card/). These are standard public prices and do not reflect any contractual or negotiated pricing.

The file format is a JSON array of objects:

```json
[
  { "key": "FULLSTACK_MONITORING", "name": "Full-Stack Monitoring", "price": "0.01", "currencyCode": "USD" },
  ...
]
```

Each entry needs:
- **`key`** — the DPS capability identifier (must match the keys used in the calculator pages)
- **`name`** — display name
- **`price`** — unit price as a string
- **`currencyCode`** — currency code (e.g. `USD`)

To use contractual or negotiated pricing instead, replace the prices in `ratecard.json` with values from your Dynatrace contract.

## Tech Stack

- Pure HTML / CSS / JavaScript — no build step, no frameworks
- Google Fonts (Inter)
- Designed with Dynatrace brand colours

## License

See [LICENSE](../LICENSE) in the repository root.
