# Pantheon Next.js: Single-Site Demo

A Drupal recipe that configures a Drupal 10.4+ site as the headless backend for a
**single** Next.js front end on Pantheon. It wires up the content model, JSON:API, OAuth,
and the Next.js module so the front end can read content and revalidate pages out of the
box.

> **Single-site variant.** This recipe backs **one** Next.js front end. For a shared
> backend serving **multiple** independent front ends — with per-site content scoping via
> a `field_next_site` reference and layered vertical recipes — use
> [`pantheon-systems-ps/pantheon_nextjs_multi_demo`](https://github.com/pantheon-systems-ps/pantheon_nextjs_multi_demo)
> instead.

## Requirements

- Drupal core 10.4 or newer.
- [`drupal/next`](https://www.drupal.org/project/next) plus `decoupled_router`,
  `consumers`, `simple_oauth`, and `pathauto` — all pulled in automatically when you
  require this package.

## What it adds

- **Page, Article, and Event content types**, with their fields and form/view displays.
- **`next.next_site.nextjs`**: registers the Next.js front end with base, preview, and
  revalidate URLs. The base URL is a recipe input (`base_url`), overridable per
  environment.
- **`nextjs` navigation menu**, with the Page content type wired to use it.
- **JSON:API** and the `linkset_endpoint` feature flag enabled for decoupled routing.

## Apply

```bash
composer require pantheon-systems-ps/pantheon_nextjs_demo
drush recipe recipes/pantheon_nextjs_demo
drush cache:rebuild
```

Set the front-end base URL for your environment:

```bash
drush recipe recipes/pantheon_nextjs_demo \
  --input=pantheon_nextjs_demo.base_url=https://your-frontend.example
```

Pair it with
[`pantheon-systems-ps/pantheon_nextjs_demo_content`](https://github.com/pantheon-systems-ps/pantheon_nextjs_demo_content)
to fill the site with ready-made sample content.
