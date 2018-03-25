# Deploy to Firebase

1. Sign in to Google Firebase using a Google account https://firebase.google.com/
2. Go to Firebase console: https://console.firebase.google.com
3. Add Firebase project: "Add project"
  - enter project name
  - remember project id
  - select country
  - "Create Project"
4. Install Firebase tools `$ npm install -g firebase-tools`
5. Sign in to Google `$ firebase login --interactive` or `$ firebase login:ci --interactive`
6. Specify project name: inside your local repository open the ".firebaserc" file and enter your project id `default: your-firebase-project-id`
7. Deploy `$ firebase deploy` and verify going to https://[your-firebase-project-id].firebaseapp.com
8. Set custom domain: back in your firebase console select your project:
  - select "Hosting" and
  - click "CONNECT DOMAIN"
  - follow the on screen instructions (also see here for details https://firebase.google.com/docs/hosting/custom-domain)
  - wait for SSL certificate provisioning (this can take several hours)
