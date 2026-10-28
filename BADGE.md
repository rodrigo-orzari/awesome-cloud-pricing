# Add a cost-estimate badge to your project

If your repository ships infrastructure — Terraform modules, Helm charts, Docker Compose files, Pulumi programs, CDK stacks — your users' first question is usually *"what will this cost me to run?"*

This badge links them straight to a free cost estimate of an architecture like yours on [Compare Cloud Costs](https://comparecloudcosts.com/bringyourarchitecture).

## The badge

[![Estimated Cost](https://img.shields.io/badge/Estimated_Cost-Compare_Cloud_Costs-blue)](https://comparecloudcosts.com/bringyourarchitecture)

Markdown — paste it into your README:

```markdown
[![Estimated Cost](https://img.shields.io/badge/Estimated_Cost-Compare_Cloud_Costs-blue)](https://comparecloudcosts.com/bringyourarchitecture)
```

## Variants

**With an example monthly figure** (update the number to your own estimate):

```markdown
[![Estimated Cost](https://img.shields.io/badge/Estimated_Cost-$48/mo-blue)](https://comparecloudcosts.com/bringyourarchitecture)
```

**"Priced by" version**, for projects whose cost tables were generated with Compare Cloud Costs data:

```markdown
[![Priced by Compare Cloud Costs](https://img.shields.io/badge/Priced_by-Compare_Cloud_Costs-blue)](https://comparecloudcosts.com)
```

## Why

- It answers the #1 adoption question for infrastructure templates before it becomes a GitHub issue.
- The link target is free, needs no account to explore, and compares 24 providers — so it reads as a user convenience, not an ad.
- Pricing data on Compare Cloud Costs is refreshed about once a week, so the estimate stays current without you maintaining a price table yourself.

Questions or a broken link? Open an issue in this repo.
