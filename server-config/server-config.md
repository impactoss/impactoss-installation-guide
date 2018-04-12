# Overview: Server configuration

The IMPACT OSS server is a Rails app.

IMPACT OSS can be configured in many different ways to suit each State's individual set up and requirements, some of which are required and some that are optional.

Before you start we recommend to to fork the source code repository from https://github.com/impactoss/impactoss-server to existing GitHub user or organisation, then

1. [Configure application settings](/server-config/application.md)
2. Optional: [Edit email templates](/server-config/email-templates.md)
3. Optional: [Configure email reminders](/server-config/reminders.md)
4. Optional: [Configure taxonomies & categories](/server-config/categories.md)
5. Optional: [Edit labels, text & translations](/server-config/locales.md)

Please note: in addition to the `master` and `production` branches that reflect the default configuration, we have also included additional demo configurations (with kind support of [Universal Rights Group Geneva](http://www.universal-rights.org/) and the [Permanent Mission of the Republic of Singapore, Geneva](https://www.mfa.gov.sg/content/mfa/overseasmission/geneva.html)):
* branch `demo-rights`:  the "Rights" configuration with SDGs disabled and compatible with the branch of the same name of the client repository (see [Client Configuration](/client-config/client-config.md)) - [click here to go to branch](https://github.com/impactoss/impactoss-server/tree/demo-rights)
* branch `demo-sgds`:  a configuration with optional SDGs enabled and compatible with the branch of the same name of the client repository (see [Client Configuration](/client-config/client-config.md)) - [click here to go to branch](https://github.com/impactoss/impactoss-server/tree/demo-sdgs)