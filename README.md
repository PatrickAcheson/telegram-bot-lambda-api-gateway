# telegram-bot-lambda-api-gateway
Detailed walkthrough of the creations of a Telegram Bot using AWS services such as Lambda and API Gateway. 

During this walkthrough I will be using the region of "eu-west-2", choose your region accordinly.
### Telegram
1. Creating bot~
2. Go to Telegram Web. Sign in or create an account.
3. Start a chat with @BotFather.
4. Type "/start".
5. Type "/newbot" to create a new bot. I named my bot "lesterchan_bot".
6. Note the HTTP API access token that @BotFather will reply you after you created the bot.

### AWS Lambda
1. Go to [AWS Lambda](https://eu-west-2.console.aws.amazon.com/lambda/home?region=eu-west-2#/).
2. Navigate to the "Create Function" and click it.
3. Under the "Author from scratch" screen, select it and enter a Fuction name. I am using "telegram-awp".
4. Under run time, select "Python 3.6"
5. Select "Change default execution role" at the bottom and use "Create a new role from AWS policy templates", name the Role accordinly and select "Basic Lambda@Edge permissions" under the Policy templates.
7. Select "Create Fuction".


### API Gateway
1. From home select use "API Gateway" from search bar. Select "Create API".(https://eu-west-2.console.aws.amazon.com/apigateway/).
2. We will be using "REST API" and click "build". Inside Settings input the API name.
3. You will be redirected to the "Resources" page.
4. Click "Actions" and "Create Method" on the dropdown menu on the left, choose "ANY" and click on the "tick" icon.
5. Now, you will see the "/ - ANY - Setup" page on the right.
6. Tick the option "Use Lambda Proxy integration" and Select "Save".


### Adding script
1. Navigate back to the Lambda page and click on your fuction.
2. In "Fuction overview" and the"code" tab, paste the python code from below.
3. Change the code accordinly.


### Set Telegram Webhook
Replace <ACCESS_TOKEN> with your Telegram HTTP API access token obtained in the first step.
Replace <INVOKE_URL> with your Invoke URL obtained in the previous step.
Run this command:

$ curl --data "url=<INVOKE_URL>" "https://api.telegram.org/bot<ACCESS_TOKEN>/setWebhook"

You should get back a response similar to this:

$ {"ok":true,"result":true,"description":"Webhook was set"}

### Testing
1. Using the link FatherBot provided you can test the bot, this this current script it should reverse the input.
