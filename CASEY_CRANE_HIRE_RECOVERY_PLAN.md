# Casey Crane Hire website recovery plan

## Critical corrections

The nameservers `ns1.supercp.com` through `ns4.supercp.com` are reseller
nameservers used by **Hosting.com (formerly A2 Hosting)**. They do **not**, by
themselves, establish that Crazy Domains hosts the website. Hosting.com's
[Anycast DNS documentation](https://kb.hosting.com/docs/anycast-dns) identifies
these nameservers.

The Casey domain's MX records point to Google. This explains why Microsoft
Copilot could not access `info@caseycranehire.com.au`: the address appears to
be a **Google-hosted mailbox, not a Microsoft Outlook mailbox**.

> [!WARNING]
> Do not change the nameservers during the investigation. A nameserver change
> could interrupt both the Google-hosted Casey email and the website.

## Immediate action

### 1. Identify the account owner and providers

Search Ben's email and bank/card records for all of the following:

- A2 Hosting
- Hosting.com
- Crazy Domains
- Dreamscape
- `caseycranehire.com.au`
- `190.92.139.203`
- hosting renewal
- cPanel login

Record the account holder, customer number, billing email, renewal date, and
support contact associated with every match. Treat the domain registrar and
web host as separate roles: they may be different companies.

### 2. Preserve the existing site before intervention

Before restoring, publishing, reinstalling, or changing configuration, obtain
a complete backup of:

- website files;
- database;
- DNS zone;
- SSL configuration; and
- existing logs, if available.

Keep an untouched copy of the backup and record when and from whom it was
obtained.

### 3. Escalate the HTTP 403 without overwriting the site

If the records establish an A2 Hosting or Hosting.com account, contact
Hosting.com support with the following message:

> Our domain caseycranehire.com.au uses ns1.supercp.com through
> ns4.supercp.com and resolves to 190.92.139.203. Both the www and non-www
> versions return HTTP 403 from LiteSpeed. Please confirm the hosting account
> status, document root, file permissions, index file, .htaccess rules and
> Imunify/security blocks. Do not reinstall, delete or overwrite the existing
> website. Preserve a backup before making changes.

Contact Crazy Domains only if account records establish that it holds the
domain registration or hosting. Nameserver identity alone is not evidence that
Crazy Domains provides either service.

### 4. Validate privately before cutover

After the host identifies and remedies the cause, verify the recovered site in
a private preview or local hosts-file test. Check the home page, navigation,
forms, media, mobile layout, HTTPS certificate, redirects, and any
database-backed functionality before making the recovery public.

## Priority order

| Priority | Action |
| ---: | --- |
| 1 | Identify the actual registrar and hosting-account owner. |
| 2 | Back up the unreleased website and configuration. |
| 3 | Have Hosting.com/A2 investigate the 403 without overwriting files. |
| 4 | Verify the restored site privately before public cutover. |
| 5 | Correct Google Business Profile and directory listings. |
| 6 | Preserve Linkeo evidence and handle those domains through the dispute process. |

## Investigation guardrails

- Do not change nameservers while ownership, hosting, and mail routing are
  being established.
- Do not infer the registrar from the web host, or the web host from the
  registrar.
- Do not reinstall a CMS, replace files, reset the document root, or overwrite
  the database before a complete backup exists.
- Do not treat access failure in a Microsoft product as proof that the mailbox
  is unavailable; use the Google-hosted mail account and its administrator.
- Preserve receipts, account emails, DNS information, screenshots, support
  transcripts, and Linkeo-related evidence with dates and original metadata.
