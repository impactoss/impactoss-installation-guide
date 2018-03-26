# Heroku

#### Sign up

[Sign up](https://signup.heroku.com) for a free account and/or [log in](https://id.heroku.com/login)

#### Set up billing

Go to "account settings" > "Billing" and add your credit card details.

#### Create New App

Create New App with a name of your liking.

#### Set up config variables  

Go to "Settings", click "Reveal Config Vars" and add
- `RAILS_ENV`: `production`
- `RACK_ENV`: `production`
- `RAILS_LOG_TO_STDOUT`: `enabled`
- `RAILS_SERVE_STATIC_FILES`: `enabled`
- `LANG`: `en_US.UTF-8`
- `DATABASE_TIMEOUT`: `9000`
- `DATABASE_POOL_SIZE`: `20`  
- `AWS_BUCKET_REGION`: e.g. `us-west-2`, your AWS bucket region [see AWS S3](server-installation/aws.md)
- `AWS_ACCESS_KEY_ID`: your AWS access key id [see AWS S3](server-installation/aws.md)
- `AWS_SECRET_ACCESS_KEY`: your AWS secret access key [see AWS S3](server-installation/aws.md)
- `SADATA_SECRET_KEY_BASE`: a random secret key, generated e.g. using 'rake secret' or [online (eg 512-bit, enable Hex)](http://www.allkeysgenerator.com/Random/Security-Encryption-Key-Generator.aspx)

#### Recommended: install Heroku CLI

- Go to https://devcenter.heroku.com/articles/heroku-cli and follow the download and installation instructions.
- Once installed login to your Heroku account

#### Set up database

Go to "Resources"
- Search for "Heroku Postgres" add-on
- Select and provision "Hobby Dev" for staging/development or "Standard 0" for production (you can also upgrade later)

Create the database tables either using
- Heroku dashboard console: More > Run Console: `rake db:migrate`; or
- Heroku CLI: run `heroku run rake db:migrate --app your-app`

Initialise data according to Seed file (see [categories](/server-config/categories.md)) either using
- Heroku dashboard console: More > Run Console: `rake db:seed `; or
- Heroku CLI: run `heroku run rake db:seed --app your-app`

#### Connect with GitHub repository

Go to "Deploy"
- Select Deployment method "GitHub"
- Connect to GitHub
- Select and connect to repository (previously forked to a personal or organization account, see [Fork server source code](/server-config/source-code.md))
- Manually deploy from "master" branch for staging/development or "production" branch for production; or
- Enable automatic deploys

#### Upgrade dynos

By default Heroku will be set up with free dynos for your application server "web" and the email scheduler "clock". These free dynos will automatically "go to sleep" when idle resulting in long wait times - to prevent this upgrade to the "Hobby" plan.

Go to "Resource"
- Click "Upgrade to Hobby..."
- Select "Hobby" to upgrade the "web" dyno

#### Initialise MailGun

Go to "Resources"
- Search for "MailGun" add-on
- Select and provision "Starter"

This will add the following config variables
- `MAILGUN_API_KEY`
- `MAILGUN_DOMAIN`
- `MAILGUN_PUBLIC_KEY`
- `MAILGUN_SMTP_LOGIN`
- `MAILGUN_SMTP_PASSWORD`
- `MAILGUN_SMTP_PORT`
- `MAILGUN_SMTP_SERVER`

To set up MailGun with your custom domain, see [MailGun](/server-installation/mailgun.md)

#### Optional: Custom API URL

To set a custom domain for your server API go to "Settings" and add your domain name, e.g. a subdomain `api.yourdomain.org`

Then go to your domain registrar and update the DNS records by adding a CNAME record pointing to `api.yourdomain.org.herokudns.com`

#### Recommended: Upgrade database

We recommend to upgrade to the "Standard Postgres" databse for production, following the instructions provided here:
https://devcenter.heroku.com/articles/upgrading-heroku-postgres-databases