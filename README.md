# shanevaldez.com

Shane Valdez's personal site. One static page, hosted free on GitHub Pages.

**Live:** https://shanevaldez.com
**Last updated:** November 4, 2026

## Where we left off

The site is a single black screen with small white text, centered:

```
Shane Valdez

Acific Labs Founder
SuperFile Founder & Inventor
Super Innovation Company Founder
The Okay Company Founder
```

- The name opens an email to shane@superfile.com.
- Acific Labs, SuperFile and The Okay Company link to acific.com, superfile.com and okaycompany.com.
- Super Innovation Company has no link, because superinnovationcompany.com only forwards to superfile.com.
- No cities, no social links on the page, no custom fonts, no JavaScript.
- X and LinkedIn are still listed invisibly in the page head for search engines.

Nothing is broken or half done. The next step is whatever you want to change.

## Pick back up with Claude

Open Claude Code in this folder (`~/Developer/shanevaldez.com`) and paste:

> Read README.md. This is my personal site, shanevaldez.com, hosted on GitHub Pages from this repo. I want to: ___

Claude can edit `index.html`, push to `main`, and confirm the live site updated.

## How to change the site

1. Edit `index.html`.
2. Commit and push to `main`:

   ```bash
   git add -A && git commit -m "Describe the change" && git push
   ```

3. GitHub Pages republishes in about a minute. Hard refresh to see it.

When you change the roles, also update the matching text in the page head:
the `<title>`, the `description` and `og:description` tags, and the `jobTitle` list in the JSON-LD block.
Search engines and link previews use those.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole site |
| `favicon.svg`, `apple-touch-icon.png` | Browser tab and home screen icons |
| `og.png` | Preview image when the link is shared (your name on black) |
| `CNAME` | Tells GitHub Pages to serve the site at shanevaldez.com. Don't delete it. |
| `.nojekyll` | Tells GitHub Pages to serve files as is |
| `shane.png` | Old Super Innovation Company seal. No longer used by the page. |

Every file in this repo is public, at the repo and on the site itself.

## Hosting and domain

- **Hosting:** GitHub Pages, repo `acific/shanevaldez.com`, branch `main`, root folder.
- **HTTPS:** a free certificate issued by GitHub, which renews it automatically. HTTPS is enforced.
- **Domain registrar and DNS:** NameBright.
- **Redirects:** www.shanevaldez.com and http:// both forward to https://shanevaldez.com.

DNS records at NameBright that point the domain at GitHub:

| Type | Host | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | acific.github.io |

The email records at NameBright (MX, SPF, webmail, smtp, pop, imap) were left untouched.
Don't change them unless you mean to change email.

Check hosting status:

```bash
gh api repos/acific/shanevaldez.com/pages
```

If the browser ever shows a certificate warning, re-trigger the certificate by removing and re-adding the custom domain:

```bash
gh api -X PUT repos/acific/shanevaldez.com/pages -f cname=
```

```bash
gh api -X PUT repos/acific/shanevaldez.com/pages -f cname=shanevaldez.com
```

Both commands also add commits to `main`, so run `git pull` before your next push.

## History

- **Before October 30, 2026:** the site ran on Vercel under an account nobody could access. The source code was never found.
- **October 30:** moved hosting to GitHub Pages and pointed NameBright DNS at it. Fixed the certificate error on www.
- **October 30 and 31:** a one-page site with a large serif name, then both roles, then cities.
- **October 31:** an ambitious "patent specification" version, built around Shane's four US patents. It was too complicated and was replaced within the hour.
- **October 31 to November 4:** simplified down to the current black screen, then several rounds of role wording and order.

Any earlier version can be restored from git history. For example, the patent version is commit `527edb6`.

## Facts on file for future use

These were researched for the patent version. They are not on the current page.

- Shane Ryan Valdez is the sole inventor on four granted US patents, all assigned to SuperFile, Inc.:
  [11,977,644](https://patents.google.com/patent/US11977644B2/en) (May 7, 2024),
  [12,210,637](https://patents.google.com/patent/US12210637B2/en) (January 28, 2025),
  [12,314,409](https://patents.google.com/patent/US12314409B2/en) (May 27, 2025),
  [12,554,866](https://patents.google.com/patent/US12554866B2/en) (February 17, 2026).
- The earliest priority date is July 24, 2020.
- Directing reels on Vimeo play only through the player links:
  [American Idol](https://player.vimeo.com/video/392129799),
  [Emmys](https://player.vimeo.com/video/461446120),
  [Dancing with the Stars](https://player.vimeo.com/video/461453050).
