# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The public, static information site for **llmstxtscan.org** — a transparency
page for the "llms.txt crawler bot," a research crawler that
checks websites for standard well-known files. The site's job: let any site
operator identify the crawler from its User-Agent and request exclusion. It is a
compliance/transparency artifact, so accuracy matters more than features.

**Live:** https://llmstxtscan.org

## Structure

- `index.html` — the single-page site (inline CSS, no build step).
- `CNAME` — custom apex domain (`llmstxtscan.org`). **Do not remove.**
- `.nojekyll` — disables Jekyll so the dot-directory `.well-known/` is served. **Do not remove.**
- Dogfooded well-known files (valid examples of what the crawler looks for),
  each linking back to the crawler info + contacts:
  - `llms.txt`, `llms-full.txt`, `AGENTS.md`, `robots.txt`, `sitemap.xml`
  - `.well-known/security.txt` (RFC 9116; keep the `Expires` field in the future)

## Deploy

Push to `main` → GitHub Pages rebuilds (~30s). HTTPS is enforced via a
GitHub-managed Let's Encrypt cert. DNS lives in **Cloudflare**: apex `A` records
to the GitHub Pages IPs (`185.199.108–111.153`), set **DNS-only (grey cloud, not
proxied)** so GitHub can issue and renew the certificate. After a push, verify
with e.g. `curl -sI https://llmstxtscan.org/.well-known/security.txt`.

## Editing rules (keep it accurate)

- The crawler User-Agent is `llms.txt crawler bot (+https://llmstxtscan.org; opt-out@llmstxtscan.org)`.
  Keep this string **identical** across `index.html`, `llms.txt`, and `llms-full.txt`.
- State the behavioral boundary **positively**: the crawler "accesses only
  publicly available resources, bypasses no access controls, and performs no
  writes." Do **not** claim it "never follows links" or "never fetches pages" —
  later research phases may fetch llms.txt-referenced links, and a claim you
  outgrow is worse than none.
- The opt-out (`opt-out@`) and contact (`contact@`) addresses must stay
  consistent across all files and remain live mailboxes.
- Keep the page minimal, truthful, and dependency-free (no build step / framework).

Research conducted in association with the Cloud Security Alliance.
