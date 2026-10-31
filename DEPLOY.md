# Deploying shanevaldez.com

The site is a single static page (`index.html` plus `fonts/` and icons), hosted on
GitHub Pages from the `main` branch of `acific/shanevaldez.com`. The `CNAME`
file tells Pages to serve it at shanevaldez.com.

## One-time setup

1. Create the repo and push (GitHub Pages on a free plan needs a public repo):

       gh repo create acific/shanevaldez.com --public --source . --remote origin --push

2. Turn on Pages from `main`, root folder, with the custom domain:

       gh api -X POST repos/acific/shanevaldez.com/pages -f build_type=legacy -f 'source[branch]=main' -f 'source[path]=/'
       gh api -X PUT  repos/acific/shanevaldez.com/pages -f cname=shanevaldez.com

3. At NameBright (DNS for shanevaldez.com), replace the current Vercel records with:

   | Type  | Host | Value                 |
   |-------|------|-----------------------|
   | A     | @    | 185.199.108.153       |
   | A     | @    | 185.199.109.153       |
   | A     | @    | 185.199.110.153       |
   | A     | @    | 185.199.111.153       |
   | CNAME | www  | acific.github.io      |

   Delete the existing A record for `@` (216.150.1.1) and the existing
   CNAME for `www` (…vercel-dns-016.com) first.

4. After DNS propagates (minutes to an hour), enable HTTPS:

       gh api -X PUT repos/acific/shanevaldez.com/pages -F https_enforced=true

## Updating the site

Edit `index.html`, commit, push to `main`. Pages redeploys in about a minute.
