# Email settings

The email address used by the application when sending out emails, including for user authentication and email reminders is set in:
- General: [/app/mailers/application_mailer.rb](https://github.com/impactoss/impactoss-server/blob/master/app/mailers/application_mailer.rb)
- Devise: [/config/initializers/devise.rb](https://github.com/impactoss/impactoss-server/blob/master/config/initializers/devise.rb)

> Please make sure the email domain coincides with your mail application, eg [MailGun](server-installation/mailgun.md)
