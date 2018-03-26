# Overview: Server installation

The server application requires different components that need to be set up, including
- Application server for controlling access to the database
- Task server for scheduled emails (email reminders)
- Database for storing content
- Document storage for storing documents

These can be set up in many different ways. Here we describe a specific, recommended set-up only:

1. Set up document storage using [AWS S3](/server-installation/aws.md)
2. Set up application and task server, as well as database using [Heroku](/server-installation/heroku.md)
3. Set up mail automation using [MailGun](/server-installation/mailgun.md)
