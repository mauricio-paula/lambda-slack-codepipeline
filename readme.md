This Cloudformation template creates an environment with resources to monitor and alert when any Codepipeline pipeline change status.


Setup:

Follow these steps to configure the webhook in Slack:
  1. Navigate to https://<your-team-domain>.slack.com/services/new
  2. Search for and select "Incoming WebHooks".
  3. Choose the default channel where messages will be sent and click "Add Incoming WebHooks Integration".
  4. Copy the webhook URL from the setup instructions and use it in the next section.


Parameter: 

slackchannel: Messages that are sent to the incoming webhook will be posted here.

slackuser: Messages that are sent to the incoming webhook will be posted by this user.

slackwebhookurl: Messages that are sent to the incoming webhook will be posted here.



How to deploy this stack: 

aws cloudformation create-stack --stack-name SlackAlerts \
--template-body file://cfn-alert-slack.yaml --capabilities CAPABILITY_IAM \
--parameters ParameterKey=slackchannel,ParameterValue=<change_with_your_slack_channel> \
ParameterKey=slackuser,ParameterValue=<change_with_your_slack_user> \
ParameterKey=slackwebhookurl,ParameterValue=<change_with_your_slack_webhook_url>



Resources:

- EventRule

- PermissionForEventsToInvokeLambda

- LambdaExecutionRole

- alertslack(lambda function)
