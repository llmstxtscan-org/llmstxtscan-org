# llmstxtscan.org

Public information site for the **llms.txt crawler bot** — a research
crawler that checks websites for a small set of standard, publicly
served "well-known" files. This site explains what the crawler does and lets any
operator identify it and opt out.

**Live:** https://llmstxtscan.org

## The crawler

- **User-Agent:** `llms.txt crawler bot (+https://llmstxtscan.org; opt-out@llmstxtscan.org)`
- **Opt-out:** [opt-out@llmstxtscan.org](mailto:opt-out@llmstxtscan.org) — send the domain(s) to exclude
- **Contact:** [contact@llmstxtscan.org](mailto:contact@llmstxtscan.org)
- It accesses **only publicly available resources**; it bypasses no access
  controls and performs no write actions.

## Files this site serves (it dogfoods what it researches)

| File | URL |
|------|-----|
| Info page | https://llmstxtscan.org/ |
| llms.txt | https://llmstxtscan.org/llms.txt |
| llms-full.txt | https://llmstxtscan.org/llms-full.txt |
| AGENTS.md | https://llmstxtscan.org/AGENTS.md |
| security.txt | https://llmstxtscan.org/.well-known/security.txt |
| robots.txt | https://llmstxtscan.org/robots.txt |
| sitemap.xml | https://llmstxtscan.org/sitemap.xml |

## How it's served

Static site via **GitHub Pages** on the apex domain (`CNAME` → `llmstxtscan.org`).
Push to `main` and Pages redeploys in ~30s; HTTPS is enforced (GitHub-managed
Let's Encrypt). `.nojekyll` ensures the `.well-known/` directory is served
(Jekyll would otherwise hide dot-directories). DNS is in Cloudflare: apex `A`
records to GitHub Pages IPs, DNS-only (not proxied).

---

Research conducted in association with the
[Cloud Security Alliance](https://cloudsecurityalliance.org).
