# WCH Conversation Integration Server

Starter Kit for a server side implementation on how to create an cogntitive advisor based on the Watson Conversation Service and Watson Content Hub. This sample offers convenience features to sync intents & entities with Watson Content Hub and is based on the Botkit framework which makes it easy to extend to an cogntitive advisor solution running on Slack, Facebook Messenger, Cisco Spark, Twilio IP Messanging & Microsoft Bot Framework.

Currently this sample is configured to be used either in an bot scenario with an robot or with slack.

## Core Idea
The value of this solution is simple and powerful: We let the Watson Conversation Service define the flow & structure of the conversation. All content is created & managed in Watson Content Hub and retrieved dynamically for the right response node. Therefore we can easily enhance the conversation responses with images, videos, ... and switch the language of the conversation as needed.

## How to get started
Clone the repository:
```
git clone https://github.ibm.com/sterbling/wch-conversation-integration-server.git
```

If you want to start the server locally you have to create a valid `dch_vcap.json` file in the root directory of the application. As a starting point you can use `dch_vcap_sample.json` where you just have to put in all credentials needed.

NOTE: If you are not interessted in the slack integration of this sample you can omit the bot_config completely.

Example:
```json
{
    "tone_analyzer": [
        {
            "credentials": {
                "url": "<Copy the credentials from bluemix>",
                "username": "<Copy the credentials from bluemix>",
                "password": "<Copy the credentials from bluemix>"
            },
            "syslog_drain_url": null,
            "label": "tone_analyzer",
            "provider": null,
            "plan": "standard",
            "name": "wch-toneanalyzer",
            "tags": [
                "watson",
                "ibm_created",
                "ibm_dedicated_public",
                "lite"
            ]
        }
    ],
    "conversation": [
        {
            "credentials": {
                "url": "<Copy the credentials from bluemix>",
                "username": "<Copy the credentials from bluemix>",
                "password": "<Copy the credentials from bluemix>"
            },
            "syslog_drain_url": null,
            "label": "conversation",
            "provider": null,
            "plan": "standard",
            "name": "wch-conversation",
            "tags": [
                "watson",
                "ibm_created",
                "ibm_dedicated_public",
                "lite"
            ]
        }
    ],
    "user-provided": [
        {
            "credentials": {
                "baseurl": "<Copy the baseUrl from the WCH Authoring UI>",
                "hosturl": "<Copy the hosturl from the WCH Authoring UI>",
                "tenantid": "<Copy the tenantid from the WCH Authoring UI>",
                "username": "<A valid wch user>",
                "password": "<The password>"
            },
            "syslog_drain_url": "",
            "label": "user-provided",
            "name": "wch_config",
            "tags": []
        },
        {
            "credentials": {
                "clientid": "<Client ID of your Slack Application>",
                "clientsecret": "<Client Secret of your Slack Application>",
                "verificationtoken": "<Verification Token of your Slack Application>"
            },
            "syslog_drain_url": "",
            "label": "user-provided",
            "name": "bot_config",
            "tags": []
        }
    ]
}
```