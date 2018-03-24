# Email templates

The email templates (html) can be configured in [/app/views/devise/mailer](https://github.com/impactoss/impactoss-server/tree/master/app/views/devise/mailer).

Currently the application uses

### Password reset instructions

The template is [/app/views/devise/mailer/reset_password_instructions.html.erb](https://github.com/impactoss/impactoss-server/blob/master/app/views/devise/mailer/reset_password_instructions.html.erb)

You have access to the following fields and entities:
- text fields (e.g. `t '.request_reset_link_msg'` or `t(:hello).capitalize`), see [Labels & translations](server-config/locales.md)
- `@resource`: all receiving user fields, e.g. `@resource.email`

> For more details see https://github.com/lynndylanhurley/devise_token_auth#email-template-overrides
