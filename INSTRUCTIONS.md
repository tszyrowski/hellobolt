# Basic setup

1. **OAuth and Permissions** page and add the Bot Token scope `chat:write` to be able to send messages via app/bot
2. App’s **Basic Information** page add the App-Level Token, with scope `connections:write` to be able to send messages via app/bot.
3. Authorize & install the app to create an oAuth access token starting with `xoxb-*`.
4. Create `.env`
```
SLACK_SIGNING_SECRET=<Signing Secret under the App Credentials header in the Basic Information>
SLACK_BOT_TOKEN=<token under “Tokens” in Basic Information > App-Level Tokens xoxb-*>
SLACK_APP_TOKEN=<app level token of installed the app, under “App-Level Tokens” in Basic Information > Install app. xapp-*>
```
5. Initialize node project:
```
$ npm init
$ npm install @slack/bolt
$ npm install dotenv
```
6. Start ngrok in its own tab on your local machine: `$ ngrok http 3000`
7. Create a file ‘app.js’.
8 Start Bolt app `$ nodemon app.js`
9 App’s **Event Subscriptions** page and enable events
10. Add the Request URL: https://YOUR_NGROK_URL.ngrok.io/slack/events
11. Subscribe to a bot event by clicking the Add Bot User Event button and entering `app_home_opened` into the input box.
12. Save Changes.
13. We subscribed to the app_home_opened event and sent a message to the user when they opened a DM with our bot.