# BridgeOps Professional Website

This folder contains the Jekyll source for bridge-ops.ai hosted on Cloudflare Pages.

## Stack

- Ruby 4.0.5 (Homebrew)
- Jekyll 4.x
- jekyll-feed, jekyll-sitemap, jekyll-seo-tag

## Local Setup (macOS)

1. Install Homebrew Ruby.

```bash
brew install ruby
```

1. Use Homebrew Ruby for this session.

```bash
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
```

1. Configure Bundler for local install path.

```bash
bundle config set path vendor/bundle
```

1. Configure eventmachine native build flags (required on this machine).

```bash
bundle config set --local build.eventmachine "--with-cxx=/opt/homebrew/opt/llvm/bin/clang++ --with-cppflags=-I/opt/homebrew/opt/llvm/include/c++/v1"
```

1. Install dependencies.

```bash
bundle install
```

## Build and Serve

Build static site:

```bash
bundle exec jekyll build
```

Serve locally:

```bash
bundle exec jekyll serve
```

## Cloudflare Pages Build Settings

- Build command: bundle exec jekyll build
- Output directory: _site
- Environment variable: JEKYLL_ENV=production
