# General application settings

### Application config

The application configuration file is
[/config/application.rb](https://github.com/impactoss/impactoss-server/blob/master/config/application.rb).

Here you can set
- Timezone, e.g. `config.time_zone = 'Pacific/Auckland'`

### Environment settings

Different environment settings are available in
[/config/environments](https://github.com/impactoss/impactoss-server/blob/master/config/environments)

Specifically, these are
- Production: [/config/environments/production.rb](https://github.com/impactoss/impactoss-server/blob/master/config/environments/production.rb)
- Development: [/config/environments/development.rb](https://github.com/impactoss/impactoss-server/blob/master/config/environments/development.rb)
- Staging: [/config/environments/staging.rb](https://github.com/impactoss/impactoss-server/blob/master/config/environments/staging.rb)
- Test: [/config/environments/test.rb](https://github.com/impactoss/impactoss-server/blob/master/config/environments/test.rb)

To set up your site, you will at least need to configure the procution configuration, in particular:
- Mail server domain: `config.action_mailer.smtp_settings.domain`
- Mail server URL host: `config.action_mailer.default_url_options.host`
- Mail server asset host: `config.action_mailer.asset_host`
