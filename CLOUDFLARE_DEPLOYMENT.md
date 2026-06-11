# Cloudflare Pages Deployment

## Repository connection

1. Push this site directory to a dedicated GitHub repository.
1. In Cloudflare, open **Workers & Pages** and create a Pages project.
1. Connect the GitHub repository and production branch.

## Build configuration

- Framework preset: Jekyll
- Build command: `bundle exec jekyll build`
- Build output directory: `_site`
- Root directory: `/` when this directory is the repository root

Environment variables:

- `JEKYLL_ENV=production`
- `RUBY_VERSION=4.0.5`

Cloudflare builds on Linux and does not require the local macOS `eventmachine` compiler override in `.bundle/config`.

## Custom domains

1. Add `bridgeops.ai` as the primary custom domain.
1. Add `www.bridgeops.ai` as a secondary domain.
1. Keep the redirect in `_redirects` so `www` resolves permanently to the apex domain.
1. Enable **Always Use HTTPS** in Cloudflare SSL/TLS settings.
1. Use **Full (strict)** SSL mode after the Pages certificate is active.

## Post-deployment checks

- Confirm `/`, `/en/`, `/projects/`, `/projekte/`, `/blog/`, and `/blog/en/` return HTTP 200.
- Confirm `https://www.bridgeops.ai/` redirects to `https://bridgeops.ai/`.
- Confirm `/robots.txt`, `/sitemap.xml`, `/_headers`, and redirects are deployed as expected.
- Inspect canonical and `hreflang` tags in rendered page source.
- Enable Cloudflare Web Analytics only after the privacy approach is approved.

## Launch TODOs (Confirmed)

- Create and configure `hello@bridgeops.ai` mailbox routing before launch.
- Keep a separate dedicated repository for `bridgeops.ai` site source.

## Build troubleshooting

If Cloudflare does not honor `RUBY_VERSION`, set the Pages build image to the latest available version and select a supported Ruby 3.3+ runtime. Jekyll 4.4 is compatible with the site source.
