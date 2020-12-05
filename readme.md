# Quote Bot
## A Fun Way To Remember What's Being Said on Discord

![alt text](https://github.com/jeffcampbell/quote-bot/blob/main/docs/example-quote.png "Example Quote")

![alt text](https://github.com/jeffcampbell/quote-bot/blob/main/docs/example-meme.png "Example Meme")

How often do you see a joke, quip, or ridiculous statement on Discord that you'd like to keep for posterity? This simple bot uses an emoji reaction to save messages, and a command to re-surface those messages in the future. If you like memes, you can also automatically generate a random meme with the quote.

### What you will need
Quote Bot relies on a few services to get started:
 - A discord bot
 - A google cloud project with google data store
 - A Heroku account
 - A Imgflip account

### Instructions
1. Clone this repository locally
2. Navigate to [http://console.cloud.google.com](http://console.cloud.google.com) and create a new project. Once the project has been created, you will need to [create a service account](https://cloud.google.com/iam/docs/creating-managing-service-account-keys). Create a key with that service account in json format and save it to the quote-bot directory (I usually save it as "credentials.json").
3. Navigate to [https://discord.com/developers/applications](https://discord.com/developers/applications) and create a new application (Call it "Quote Bot", or whatever you would like). Select the "Bot" option and then "Add Bot". Copy the token and save it in the `bot_token.py` file.
4. From the command line, run `pip install -r requirements.txt` to install the proper packages
5. You should now be able to test your bot by running `python main.py`. If you see --welcome message-- your bot is working! You can stop the bot now as we get it ready for it's permanent home.
6. Navigate to [https://dashboard.heroku.com/apps](https://dashboard.heroku.com/apps) and create a new app. Follow the instructions in the "Deploy" tab to get your bot running in Heroku.
7. Once your bot has been pushed to Heroku, navigate to the "Config var" options in the Settings" tab. Add a new variable with the key `GOOGLE_APPLICATION_CREDENTIALS`, and the value being the json file where your google service account key is located (ex. "credentials.json"). Next, add two more config vars, `IMGFLIP_USER` and `IMGFLIP_PASSWORD`. Add your username and password from imgflip.
8. After your config vars are set up, navigate to the "Resources" tab, find your "worker" Dyno which should be `python main.py` and turn it on.

### How to add the bot to your server
1. Select your app in the Discord Developer Portal.
2. Navigate to the "oauth2" section, and under "Scopes" select "bot". Once you have selected "bot" you will see a new option called "bot permissions". You will need to give Quote Bot permissions for "View Channels", Send Messages", and "Read Message History". 
3. Copy the URL created with "scopes", and navigate to the URL in your browser. You should be able to add the bot to as many Discord servers as you would like!