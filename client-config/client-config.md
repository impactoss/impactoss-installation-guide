# Overview: Client configuration

The IMPACT OSS server is a React Javascript application.

IMPACT OSS can be configured in many different ways to suit each State's individual set up and requirements, some of which are required and some that are optional.

Before you start we recommend to to fork the source code repository from https://github.com/impactoss/impactoss-client to existing GitHub user or organisation, then

1. [Configure application settings](/client-config/application.md)
2. [Edit labels, text & translations](/client-config/locales.md)
3. Optional (required if changed on server): [Configure taxonomies](/client-config/categories.md)
4. Optional: [Configure theme & branding](/client-config/theme.md)

---

#### Demo configuration options

Please note: in addition to the `master` branch that reflects the default configuration, we have also included additional demo configurations (with kind support of [Universal Rights Group Geneva](http://www.universal-rights.org/) and the [Permanent Mission of the Republic of Singapore, Geneva](https://www.mfa.gov.sg/content/mfa/overseasmission/geneva.html)):
* branch `demo-rights`:  the "Rights" configuration with SDGs disabled and compatible with the branch of the same name of the client repository ([Server Configuration](/server-config/server-config.md))
  * Code: https://github.com/impactoss/impactoss-client/tree/demo-rights
  * Online demo: https://demo-rights.impactoss.org/
* branch `demo-sgds`:  a configuration with optional SDGs enabled and compatible with the branch of the same name of the client repository (see [Server Configuration](/server-config/server-config.md))
  * Code: https://github.com/impactoss/impactoss-client/tree/demo-sdgs
  * Online demo: https://demo-sdgs.impactoss.org/