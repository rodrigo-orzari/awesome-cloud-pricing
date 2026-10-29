<p align="center">
  <a href="https://comparecloudcosts.com/yourcloud"><img src="ccc-logo-shield-transparent.png" alt="Compare Cloud Costs logo" width="160"></a>
</p>

# Awesome Cloud Pricing — The Multi-Cloud Cheatsheet

[![Priced by Compare Cloud Costs](https://img.shields.io/badge/Priced_by-Compare_Cloud_Costs-blue)](https://comparecloudcosts.com)

A practical, no-fluff cheatsheet for what cloud infrastructure actually costs across providers — GPU rates, object storage classes, and the egress fees that quietly dominate real bills.

Maintained by the founder of [Compare Cloud Costs](https://comparecloudcosts.com), a free tool that compares pricing across **24 cloud providers**.

> **Freshness note:** Prices below are a snapshot from **October 2026**, compiled from providers' published pricing pages. Cloud prices change often — Compare Cloud Costs refreshes its pricing data **about once a week**, so check the linked pages before making a buying decision. Nothing here is "real-time" pricing, and any tool that promises you that is overselling.

---

## GPU pricing — NVIDIA H100 (80GB, SXM)

On-demand list prices, normalized to $ per GPU-hour (multi-GPU nodes divided by GPU count). US regions.

| Provider | $ / GPU-hour | Notes |
|---|---:|---|
| RunPod (Community Cloud) | ~$2.69 | Per-second billing; capacity varies |
| Lambda | ~$3.29–3.99 | No egress fees |
| Together AI | ~$3.99 | Cluster pricing available |
| DigitalOcean | ~$4.41 | Per-second, 5-min minimum |
| Nebius | ~$4.50 | |
| CoreWeave | ~$6.16 | Sold as 8-GPU nodes |
| AWS (p5.48xlarge) | ~$6.88 | Capacity Blocks can be lower |
| Azure (ND H100 v5) | ~$6.98 | |
| Oracle Cloud (BM.GPU.H100.8) | ~$10.00 | Bare-metal 8-GPU |
| Google Cloud (A3) | ~$10.98 | Spot is dramatically cheaper |

**The takeaway:** the same H100 silicon rents for ~$2.70/hr at a specialist and ~$11/hr at a hyperscaler — a 4× spread. What the premium buys is ecosystem, compliance, and SLAs, not faster GPUs. Whether that's worth it is a workload question.

→ Compare current GPU rates across all 24 providers: [comparecloudcosts.com/dashboard?product=gpu](https://comparecloudcosts.com/dashboard?product=gpu)

---

## Object storage — storage classes compared

Per GB-month, US regions, hot tier first.

| Provider / class | $ / GB-month | Retrieval fee | Min. duration | Notes |
|---|---:|---|---:|---|
| AWS S3 Standard | $0.023 | — | — | First 50 TB tier |
| Google Cloud Storage (Standard) | ~$0.020 | — | — | |
| Azure Blob (Hot) | ~$0.018 | — | — | |
| Cloudflare R2 (Standard) | $0.015 | — | — | **$0 egress** |
| AWS S3 Standard-IA | $0.0125 | $0.01/GB | 30 days | |
| Cloudflare R2 (Infrequent Access) | $0.010 | $0.01/GB | 30 days | **$0 egress** |
| Wasabi | ~$0.008 | — | 90 days | No egress or API fees |
| Backblaze B2 | ~$0.006 | — | — | Egress free up to 3× stored data |
| AWS S3 Glacier Instant Retrieval | $0.004 | per-request | 90 days | Millisecond access |
| AWS S3 Glacier Deep Archive | $0.00099 | $0.02/GB+ | 180 days | ~$1/TB-month; hours to restore |

**The takeaway:** storage itself is rarely the problem. At 100 TB, the difference between the priciest and cheapest hot tier is a few hundred dollars a month. Egress (next section) is where bills explode — model storage + egress + requests together, never storage alone.

→ Storage comparison: [comparecloudcosts.com/dashboard?product=storage](https://comparecloudcosts.com/dashboard?product=storage)

---

## Egress — data transfer out to the internet

Per GB, first pricing tier, US regions. This is the fee nobody budgets for.

| Provider | $ / GB egress | Notes |
|---|---:|---|
| Cloudflare R2 | **$0.00** | Free on all classes |
| Backblaze B2 | **$0.00** up to 3× stored data | Then $0.01/GB |
| Lambda | **$0.00** | |
| CoreWeave | ~$0.05 | |
| Azure | ~$0.087 | First 100 GB/mo free |
| AWS | $0.09 | First 10 TB; steps down to $0.05 above 150 TB. First 100 GB/mo free |
| Google Cloud | ~$0.12 | Premium network tier |

**Worked example:** serving 10 TB/month of images directly from S3 costs ~**$913/month in egress alone**. The same data on R2 costs **$0**. Fronting S3 with CloudFront helps (the S3→CloudFront hop is free), but you still pay CloudFront's rates.

Watch the hidden multipliers too: AWS NAT Gateway adds $0.045/GB in processing on top of egress for traffic routed through it — a free S3 VPC endpoint avoids that entirely.

→ Networking comparison: [comparecloudcosts.com/dashboard?product=networking](https://comparecloudcosts.com/dashboard?product=networking)

---

## Estimate your whole architecture, not just line items

Line-item prices don't tell you what *your* stack costs. The **AI Architect** on Compare Cloud Costs takes an architecture diagram (AWS, Azure, or GCP), an existing cloud bill, or a vendor estimate, and shows what the same workload costs across providers:

→ [comparecloudcosts.com/bringyourarchitecture](https://comparecloudcosts.com/bringyourarchitecture)

Developers: the data is also available to AI assistants via the free MCP server — [`@comparecloudcosts/mcp-server`](https://www.npmjs.com/package/@comparecloudcosts/mcp-server) ([source](https://github.com/rodrigo-orzari/ccc-mcp-server)).

---

## Add the badge to your project

If your open-source project ships infrastructure templates (Terraform, Helm, Docker Compose), help your users see what it costs to run. Full instructions in [BADGE.md](BADGE.md).

[![Estimated Cost](https://img.shields.io/badge/Estimated_Cost-Compare_Cloud_Costs-blue)](https://comparecloudcosts.com/bringyourarchitecture)

---

## Contributing

Spotted a stale price or a missing provider? Open an issue or a PR with a link to the provider's official pricing page as the source. Prices without a source link won't be merged.

## License

MIT. The pricing data itself belongs to the respective providers; this cheatsheet is a compilation for reference.
