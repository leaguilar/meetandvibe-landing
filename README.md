# meet&vibe

The landing page for **meetandvibe.com**. Real-life connections, starting with group walks around Berlin.

## Develop locally

This is a static website: HTML, CSS, a small JavaScript enhancement, and original SVG illustrations. No package installation or build step is required.

```sh
cd /workspace/meetandvibe-landing
python3 -m http.server 4173 --bind 0.0.0.0
```

Open port 4173 in your local browser. Check the page on mobile and desktop; navigation, anchor links, and the expandable FAQs work without JavaScript. The script only updates the copyright year. Fonts are self-hosted and their licenses are in `assets/fonts/`.

## Publish with GitHub Pages

1. Push the site to the `main` branch of `leaguilar/meetandvibe-landing`.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Choose **main** and **/ (root)**, then **Save**.
5. Set **Custom domain** to `meetandvibe.com` and save. The included `CNAME` file already declares this domain; keep it in the repository.
6. Connect the DNS records below. After GitHub's DNS check and certificate provisioning finish, enable **Enforce HTTPS** in Pages settings.

The `.nojekyll` file tells Pages to serve these static files directly. No workflow or build credentials are needed. Future pushes to `main` publish updates once Pages is enabled. The default project address is `https://leaguilar.github.io/meetandvibe-landing/`; after the custom domain is active GitHub redirects traffic to the domain.

GitHub Pages must be available for the repository's visibility and account plan. If Pages settings are unavailable, check repository administrator access and the account's Pages eligibility.

## Connect the Namecheap domain

First check **Namecheap → Domain List → meetandvibe.com → Manage → Nameservers**. These instructions apply when the domain uses Namecheap BasicDNS or PremiumDNS. If it uses custom nameservers, make these records at the DNS provider those nameservers identify. Do not switch nameservers without first preserving the domain's other DNS records.

Under **Advanced DNS → Host Records**, add:

| Type | Host | Value | TTL |
| --- | --- | --- | --- |
| A Record | `@` | `185.199.108.153` | Automatic |
| A Record | `@` | `185.199.109.153` | Automatic |
| A Record | `@` | `185.199.110.153` | Automatic |
| A Record | `@` | `185.199.111.153` | Automatic |
| CNAME Record | `www` | `leaguilar.github.io` | Automatic |

The `www` CNAME value is only the hostname: no `https://` and no repository path. GitHub will redirect `www.meetandvibe.com` to the configured apex domain when both are correctly configured.

Replace conflicting A, AAAA, ALIAS, CNAME, parking, or URL Redirect records for **only `@` and `www`**. Preserve MX, TXT, email-related records, and records for other subdomains. Old AAAA records pointing elsewhere can cause intermittent failures even when A records are correct. IPv6 is optional; the four A records above are sufficient.

DNS changes can take up to 24–48 hours to propagate. GitHub provisions the HTTPS certificate after DNS points to Pages; check Pages settings if **Enforce HTTPS** is not available immediately. If the domain already has restrictive CAA records, confirm they allow GitHub's certificate authority, `letsencrypt.org`.

### Verify domain ownership (recommended)

In the GitHub account settings, open **Pages → Add a domain**, enter `meetandvibe.com`, and follow GitHub's verification instructions. GitHub provides a unique TXT record. Add that exact host and value in Namecheap and click **Verify** in GitHub. Keep the TXT record after verification. Its value is account-specific and is not stored in this repository.

### Verify the result

```sh
dig +short meetandvibe.com A
dig +short www.meetandvibe.com CNAME
curl -I https://meetandvibe.com
curl -I https://www.meetandvibe.com
```

The apex should resolve to the four GitHub IP addresses; `www` should point to `leaguilar.github.io`. HTTPS should load the landing page, and `www` should redirect to the apex domain. Also check **Settings → Pages** and the repository's Pages deployment run for errors.

References: [GitHub custom domain documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site), [GitHub domain verification](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages), [Namecheap DNS records](https://www.namecheap.com/support/knowledgebase/article.aspx/319/2237/how-can-i-set-up-an-a-address-record-for-my-domain/).

## Content and launch status

- The app and first Berlin experiences are marked **coming soon**. Walk descriptions are illustrative; there are no advertised dates or bookable events.
- There is no waitlist, account system, analytics, cookie tracking, or signup form. The main button takes visitors to the first-walks section.
- Before operating the commercial site, supply the actual company details for an Impressum and any applicable privacy notice. Legal identity and contact details have not been invented for this draft.
- When an app or signup destination is ready, update the calls to action and the launch FAQ in `index.html`.

All illustration assets were created for this site. Instrument Serif and Manrope are distributed under the SIL Open Font License; their license notices are included.
