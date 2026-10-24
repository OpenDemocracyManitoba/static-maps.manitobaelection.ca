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

## Secret scan

The Phase A §7.2 scan (no `.git`, `.env`, `.ftpconfig`, `.htpasswd`, `debug.log`, `*.php`, `*.sql*`; no `DB_PASSWORD`/`AUTH_KEY`/private keys/`phpinfo()`/`mysql_connect` in any text file) found nothing.

Source: the export tarball `src/maps.manitobaelection.ca.tar.gz`, sha256 `fa790f65521497a4ef379f334199fa2ae49a48b162a3de63df8178bae85d4a2a`.
