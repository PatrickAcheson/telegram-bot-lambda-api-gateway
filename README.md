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

![image](https://user-images.githubusercontent.com/90014630/152596572-fb346a34-a083-4a26-ae42-797dd65defce.png)

3. Under the "Author from scratch" screen, select it and enter a Fuction name. I am using "telegram-awp".

![image](https://user-images.githubusercontent.com/90014630/152596827-0f27444b-6ba6-447b-af7f-dc068f513e52.png)


4. Under run time, select "Python 3.6"

![image](https://user-images.githubusercontent.com/90014630/152596982-3559cf53-7bf7-4eeb-85e7-c758049e8ee8.png)

5. Select "Change default execution role" at the bottom and use "Create a new role from AWS policy templates", name the Role accordinly and select "Basic Lambda@Edge permissions" under the Policy templates.

![image](https://user-images.githubusercontent.com/90014630/152597102-6c683def-8d72-4a6c-a2d6-55be19c7fb84.png)

6. Select "Create Fuction".

![image](https://user-images.githubusercontent.com/90014630/152597132-6085d25d-cc1c-4d01-b044-55415cef5b1d.png)


### API Gateway

1. From home select use "API Gateway" from search bar. Select "Create API".(https://eu-west-2.console.aws.amazon.com/apigateway/).

![image](https://user-images.githubusercontent.com/90014630/152597272-8bd82b90-86b4-42d3-87a5-3d7bb3637604.png)


3. We will be using "REST API" and click "build". Inside Settings input the API name.

![image](https://user-images.githubusercontent.com/90014630/152597373-68eeebb5-650b-40d7-83f3-92d4b4914853.png)


5. You will be redirected to the "Resources" page.
7. Click "Actions" and "Create Method" on the dropdown menu on the left, choose "ANY" and click on the "tick" icon.

![image](https://user-images.githubusercontent.com/90014630/152597533-172fef43-26a3-4875-8695-470e19dc81d2.png)

9. Now, you will see the "/ - ANY - Setup" page on the right.
10. Tick the option "Use Lambda Proxy integration" and Select "Save".

![image](https://user-images.githubusercontent.com/90014630/152597996-6d4b2d96-bd1c-45a4-bbb5-22ceadc873aa.png)


### Adding script
1. Navigate back to the Lambda page and click on your fuction.

![image](https://user-images.githubusercontent.com/90014630/152598453-a8f9f6e2-8a8a-4441-bdb3-39b5f730a454.png)


3. In "Fuction overview" and the "code" tab, paste the python code from below.
4. Change the code accordinly.

![image](https://user-images.githubusercontent.com/90014630/152598348-ea7467e0-28f9-4ff2-a13c-17b2f6652b22.png)


5. Select "Deploy"

![image](https://user-images.githubusercontent.com/90014630/152598379-db353abe-4756-4e3b-8941-5e7b652bf7f5.png)


### Set Telegram Webhook
Replace <ACCESS_TOKEN> with your Telegram HTTP API access token obtained in the first step.
Replace <INVOKE_URL> with your Invoke URL obtained in the previous step.
Run this command:

//$ curl --data "url=<INVOKE_URL>" "https://api.telegram.org/bot<ACCESS_TOKEN>/setWebhook"

You should get back a response similar to this:

//$ {"ok":true,"result":true,"description":"Webhook was set"}

### Testing
1. Using the link FatherBot provided you can test the bot, this this current script it should reverse the input.

![image](https://user-images.githubusercontent.com/90014630/152598535-6afbc056-1361-40a0-b8eb-1d12cfc3bf27.png)

