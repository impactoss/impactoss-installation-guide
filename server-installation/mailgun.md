### MailGun

#### Sign up with MailGun
https://signup.mailgun.com/new/signup

---

#### Add a custom domain

> Please note: MailGun often requires to contact support to enable your account - a measure they have in place against abuse

- Go to https://app.mailgun.com/app/domains/new and enter your domain, ideally a subdomain, e.g. `mg.yourdomain.org`
- Then follow the steps provided to verify and configure your domain

---

#### Update your MailGun configuration in Heroku

- `MAILGUN_API_KEY`
- `MAILGUN_DOMAIN`
- `MAILGUN_SMTP_LOGIN`
- `MAILGUN_SMTP_PASSWORD`
- `MAILGUN_PUBLIC_KEY` (from https://app.mailgun.com/app/account/security)

See also [Heroku](/server-installation/heroku.md)
