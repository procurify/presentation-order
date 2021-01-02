# Presentation Order
A Serverless AWS Lambda Function that posts a randomized presentation order every two weeks to Slack

# How It Works
This app is scheduled to run every Thursday at 8 am and will post a message to the associated
Slack Channel if the Thursday falls on a Demo Day.

## Environment Variables
Currently, environment variables are provided on AWS Lambda:
- SLACK_OAUTH_TOKEN - used to authenticate app on Slack
- TEAM_LIST - list of existing engineering squads at Procurify
- SLACK_SIGNING_SECRET - signing secret used to verify message posts to Slack

One other key variable is the list of valid demo days - this is currently hardcoded in the
`verify_is_valid_demo_day` in `utils.py`. In the current state of the app, this list will
need to be updated before the end of 2021.

## Slack Commands
Currently, there is only one command that is available to users.

`/get-demo-order` - This slash command will return a randomized presentation order on demand.

To add more commands visit the Demo Day Order app on Slack. 

# How To Deploy
The following steps require your AWS credentials to be set up already.

## Setting Up Your Environment
1. Set up Serverless on your local environment
2. Create and activate a venv for this project
3. Install dependencies
3. Export environment variables locally
i.e. `export SLACK_OAUTH_TOKEN=xxxxxxxxxxxxxxxxxxxxxxx`
4. Run project locally using ` serverless wsgi serve`

## Deploy To AWS
To deploy to AWS simply run
`serverless deploy --stage production`
