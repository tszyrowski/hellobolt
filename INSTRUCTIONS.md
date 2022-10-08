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

# Socket Mode

Socket mode you enables develop more securely using WebSockets URLs instead of public HTTP endpoints. 

1. Go to your app’s Socket Mode page and enable Socket Mode
2. Save Changes and reinstall the app
> Note: ngrok is not needed

**expected console:**
```
$ nodemon app.js
[nodemon] 2.0.12
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: js,mjs,json
[nodemon] starting `node app.js`
[INFO]  socket-mode:SocketModeClient:0 Going to establish a new connection to Slack ...
⚡️Hello World.. Bolt is running in socket mode!
[INFO]  socket-mode:SocketModeClient:0 Now connected to Slack
```
# Events API

Prep:
1. Subscribe ot `Event Subscriptions` -> `Subscribe to bot events`:
- `message.im`
- `message.mpim`
- `message.groups`
- `message.channels`
2. Save Changes, reinstall
3. Make sure `App Settings` -> `App Home` -> `Allow users to send Slash commands and messages from the messages tab` [is ticked](https://stackoverflow.com/questions/67672427/cant-send-direct-message-to-slack-bot-feature-turned-off) and **Slack client might need to be reloaded with `Ctrl+R`**

# Slash command

Prep:
1. `npm install axios`
2. Select `Slash Commands` and then select `Create New Command` called  `'/mysurvey'` with short description
3. Ensure `Interactivity & Shortcuts` -> `Interactivity` is turned on

>As the app runs in `socket mode` no URL is needed, otherwise you may needed<br/>
`Socket Mode is enabled. You won’t need to specify a Request URL.`<br/>
Otherwise add: https://YOUR_NGROK_URL.ngrok.io/slack/events

# Message menus

Prep
1. If run on URL make sure the equest URL like: https://YOUR_NGROK_URL.ngrok.io/slack/events is in `Interactivity & Shortcuts` under `Interactivity` and `Select Menus`. In **socket mode** not needed
2. Create new `Slash Commands` -> `Create a New Slash Command` with name `myweather` with some description and `Save`
