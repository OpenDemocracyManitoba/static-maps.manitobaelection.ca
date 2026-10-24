# maps.manitobaelection.ca (static archive)

Static copy of **maps.manitobaelection.ca**, taken from olddroplet (`odm-nginx-ruby-php-2018`, 159.203.24.194) on 2026-10-24, before the server was retired. Static historic election-result maps.

`site/` is the served web root as it was on disk (45 files), minus the files listed below. No crawl was needed: this site was already static.

## Serving

Serve `site/` as static files from the domain root.

## Left out of `site/`

* nothing

These were left out because they were not site content: version control, PHP, or (per the archive plan) files that should not be public. The full web root is kept in a private archive repo.

## Links to internal or old hosts

None found (`upcoming.manitobaelection.ca`, `http://www.manitobaelection.ca`, `159.203.24.194`).

## Hosting

Served from **Cloudflare Workers static assets** (Phase B of the olddroplet migration). `wrangler.jsonc`, `.gitignore`, `site/404.html` and this section are written by `hosting.py` (`python3 -I hosting.py maps.manitobaelection.ca <preview|routed|final>`).

* **Worker:** `static-maps-manitobaelection-ca`, account `Stungeye@gmail.com's Account`.
* **Deploy:** `npx wrangler@4.148.0 deploy` from the repo root. Only `site/` is uploaded.
* **Routes:** `maps.manitobaelection.ca/*` on zone `manitobaelection.ca`, over the existing proxied DNS record.
* **workers.dev:** https://static-maps-manitobaelection-ca.stungeye.workers.dev. Per-version preview URLs are off (`preview_urls: false`).
* **Serving:** `html_handling: auto-trailing-slash` (`/foo` serves `foo.html`, `/foo/` serves `foo/index.html`; the other forms 307 to those) and `not_found_handling: 404-page` (`site/404.html`, a minimal page added in Phase B).
* **http → https:** the zone setting "Always Use HTTPS" (301 at Cloudflare's edge).
* **Redirect rules:** none.
* **Rollback:** while the old origin is up, remove `routes` from `wrangler.jsonc` and deploy (or delete the route in the dashboard); the origin serves again at once. A bad version can be rolled back with `npx wrangler@4.148.0 rollback`.

## Secret scan

The Phase A §7.2 scan (no `.git`, `.env`, `.ftpconfig`, `.htpasswd`, `debug.log`, `*.php`, `*.sql*`; no `DB_PASSWORD`/`AUTH_KEY`/private keys/`phpinfo()`/`mysql_connect` in any text file) found nothing.

Source: the export tarball `src/maps.manitobaelection.ca.tar.gz`, sha256 `fa790f65521497a4ef379f334199fa2ae49a48b162a3de63df8178bae85d4a2a`.
