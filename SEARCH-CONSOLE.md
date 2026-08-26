# Search Console, and why it is not analytics

The website review found no indexed Arcifact pages in a public search.
That does not prove an indexing failure, but we currently have no way to
tell the difference between "Google has not crawled us" and "Google
crawled us and ranked us nowhere". Those need completely different
responses, and guessing between them is the thing this company objects
to.

## Why this does not break the promise

Search Console reports on **Google's own index**, not on our visitors.
It tells us which queries surfaced the site and whether pages are
indexed. It sets no cookie here, loads no script here, and gives us no
information about a person that Google did not already hold from
operating a search engine.

The privacy page says so explicitly rather than relying on the
distinction being obvious.

## To verify ownership

Two options, both one-time:

**DNS, preferred.** Add the TXT record Search Console gives you to the
`arcifact.io` zone. Nothing is added to the site, and verification
survives any redeploy.

**HTML file.** Drop `google<token>.html` in this directory and deploy.
Works, but it is a file in the tree that means nothing to a reader, and
it disappears if the tree is ever rebuilt from scratch.

Then submit `https://arcifact.io/sitemap.xml`, which already exists,
already lists every page, and is already referenced from `robots.txt`.

## What is already correct

Checked before assuming anything was wrong:

- `robots.txt` sets `Content-Signal: search=yes` and `Allow: /`
- AI training crawlers are disallowed; search crawlers are not
- `sitemap.xml` resolves and lists 16 URLs
- `robots.txt` references the sitemap
- every page carries a canonical tag

So indexing is not blocked. The gap is that nobody has ever looked.
