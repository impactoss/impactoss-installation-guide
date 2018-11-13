### Optional: Email reminders

IMPACT OSS can send email reminders to "contributors" (users responsible for contributig progress reports (or status updates) for action progress indicators (or outcome indicators)). In addition email reminders can be sent out to category managers (users responsible for overseeing a category (e.g. a Human Rights Mechanism)).

In particular there are 3 types of email reminders that get sent according to the reporting schedule that can be defined for progress indicators:
- **Report due**: sent out to contributor before a progress report is due (by default weekly starting 30 days before the next report is due)
- **Report overdue**: sent out to contributor after a progress report is due ("overdue", by default daily)
- **Category reports overdue**: sent out to category manager when a progress report is overdue for any action indicator related to a recommendation tagged with user category (by default daily)

> Note: email reminders only function when the application mailer is properly [configured](server-config/email.md) and installed (e.g. using [MailGun](server-installation/mailgun.md))

---

#### Reminder frequency

The reminder frequency and schedule for the 3 different reminders is set in [/scheduler.rb](https://github.com/impactoss/impactoss-server/blob/master/scheduler.rb:)
- Report due: `every(1.week, 'Send Due Emails', at: 'Monday 08:00') do`
- Report overdue: `every(1.day, 'Send Overdue Emails', at: '08:00') do`
- Category reports overdue: `every(1.day, 'Send Categorhy Overdue Emails', at: '08:00') do`

> For more details see https://github.com/adamwiggins/clockwork

---

#### "due" status

The "due" status flags upcoming scheduled reports that are due within a specified number of days, triggering the "Report due" email reminders. The number of days is by default set to 30 but can be changed in
[/app/models/due_date.rb](https://github.com/impactoss/impactoss-server/blob/master/app/models/due_date.rb):
`DUE_NUMBER_OF_DAYS = 30.freeze`

---

#### Reminder email subject

The reminder email subject is set in the "labels" file, see [Labels & translations](server-config/locales.md)

---

#### Reminder email templates

The email templates (both html and text) for the different reminders are set in
[/app/views/due_date_mailer](https://github.com/impactoss/impactoss-server/blob/master/app/views/due_date_mailer)

##### Report due

The templates are
[/app/views/due_date_mailer/due.en.html.erb](https://github.com/impactoss/impactoss-server/blob/master/app/views/due_date_mailer/due.en.html.erb) and [/app/views/due_date_mailer/due.en.text.erb](https://github.com/impactoss/impactoss-server/blob/master/app/views/due_date_mailer/due.en.text.erb)

You have access to the following fields and entities:
- `@manager_name`: the contributor name
- `@indicator`: all indicator fields, e.g. `@indicator.title`
- `@due_date`: all date fields, e.g. `@due_date.due_date`

##### Report overdue

The templates are [/app/views/due_date_mailer/overdue.en.html.erb](https://github.com/impactoss/impactoss-server/blob/master/app/views/due_date_mailer/overdue.en.html.erb) and [/app/views/due_date_mailer/overdue.en.text.erb](https://github.com/impactoss/impactoss-server/blob/master/app/views/due_date_mailer/overdue.en.text.erb)

You have access to the following fields and entities:
- `@manager_name`: the contributor name
- `@indicator`: all indicator fields, e.g. `@indicator.title`
- `@due_date`: all date fields, e.g. `@due_date.due_date`

##### Category reports overdue

The templates are [/app/views/due_date_mailer/category_overdue.en.html.erb](https://github.com/impactoss/impactoss-server/blob/master/app/views/due_date_mailer/category_overdue.en.html.erb) and [/app/views/due_date_mailer/category_overdue.en.text.erb](https://github.com/impactoss/impactoss-server/blob/master/app/views/due_date_mailer/category_overdue.en.text.erb)

You have access to the following fields and entities:
- `@manager_name`: the category manager name
- `@category_title`: the category title
- `@indicator`: all indicator fields, e.g. `@indicator.title`
- `@due_date`: all date fields, e.g. `@due_date.due_date`
- `@category`: all category fields, e.g. `@category.id`
