# Admin user set-up

At the outset the application is installed without any users. While users can be created using the application UI, at least one "admin" user is needed to allow assigning roles using the UI:

1. Go to your client application (https://[your-firebase-project-id].firebaseapp.com or your custom domain)
2. Register a new user: click "Register" and enter your name, email address and password
3. Set admin role for user
  - on your console (if Heroku CLI installed) run `$ heroku run rails c --app your-heroku-app`, or
  - online (Heroku dashboard: https://dashboard.heroku.com/, "More" > "Run console...") run `rails c`
  - select admin role: `r=Role.find 1`
  - select user: `u=User.last`
  - promote user: `u.roles << r`
  - go to your client UI and reload to verify, e.g. by making sure you see the additional "User admin" and "Page admin" top menu items
  - set all other roles and privileges: go to your user profile (e.g. by clicking button with your name on the top menu), click "EDIT", click "SAVE"

---
