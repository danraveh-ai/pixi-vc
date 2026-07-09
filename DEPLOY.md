# Deploying and promoting pixi.vc

## 1. Publish (GitHub Pages, free)

```bash
cd ~/Projects/pixi-vc
gh repo create pixi-vc --public --source=. --push
gh api repos/{owner}/pixi-vc/pages -X POST -f build_type=legacy -f "source[branch]=main" -f "source[path]=/"
```

The CNAME file in this repo already points GitHub Pages at pixi.vc.

## 2. DNS for pixi.vc (at your registrar)

- A records for apex `pixi.vc` -> 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
- CNAME `www` -> `<github-username>.github.io`
- In the repo settings, set custom domain to pixi.vc and enable Enforce HTTPS once the certificate is issued.

## 3. Redirect danraveh.com

danraveh.com is on GoDaddy. In GoDaddy: Domain settings -> Forwarding -> Forward to `https://pixi.vc`, type 301 (permanent), forward with masking OFF. Delete the old GoDaddy Website Builder site so it stops competing in search.

## 4. Google

- Verify pixi.vc in Google Search Console (DNS TXT record), submit sitemap.xml.
- Request indexing for the homepage.
- Update LinkedIn, Crunchbase, and NFX Signal profiles to link to pixi.vc (these backlinks are what make Google and AI models associate the domain with you).

## 5. AI assistants (ChatGPT, Claude, Perplexity, Gemini)

Already in place in this repo:
- JSON-LD Person schema in index.html
- llms.txt with a clean factual bio
- robots.txt explicitly allowing GPTBot, ClaudeBot, PerplexityBot, OAI-SearchBot, Google-Extended

What moves the needle over time:
- Consistent identity across LinkedIn / Crunchbase / Signal / press, all linking to pixi.vc.
- Occasional written content on the site (notes on fintech + AI) that AI engines can cite.
- Getting quoted or listed in third-party pages (angel lists, podcasts, articles). AI answers lean heavily on third-party corroboration, not just your own site.
