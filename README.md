# Bandwidth + OpenAI Realtime Websockets Integration - Python

<a href="https://dev.bandwidth.com/docs/voice/integrations/openai/realtime/sip">
  <img src="icon.svg" title="Bandwidth OpenAI Realtime SIP Integration Guide" alt="Bandwidth OpenAI Realtime SIP Integration Guide"/>
</a>

 # Table of Contents

* [Description](#description)
* [Pre-Requisites](#pre-requisites)
* [Environmental Variables](#environmental-variables)
* [Running the Application](#running-the-application)
* [Callback URLs](#callback-urls)
  * [Ngrok](#ngrok)

# Description

This is a sample application that demonstrates how to use the Bandwidth's Programmable Voice API with OpenAI's Realtime Websocket Interface to create a real-time AI-powered voice assistant.

# Pre-Requisites

In order to use the Bandwidth API users need to set up the appropriate application at the [Bandwidth App](https://dashboard.bandwidth.com/) and create API tokens.

To create an application log into the [Bandwidth App](https://dashboard.bandwidth.com/) and navigate to the `Applications` tab.  Fill out the **New Application** form selecting `Voice`.  All Bandwidth services require publicly accessible Callback URLs, for more information on how to set one up see [Callback URLs](#callback-urls).

For more information about API credentials see our [Account Credentials](https://dev.bandwidth.com/docs/account/credentials) page.

# Environmental Variables

The sample app uses the below environmental variables.

```sh
BW_ACCOUNT_ID      # Your Bandwidth Account ID
BW_USERNAME        # Your Bandwidth API Username
BW_PASSWORD        # Your Bandwidth API Password
OPENAI_API_KEY     # Your OpenAI API Key
TRANSFER_TO        # The phone number to transfer the call to (in E.164 format, e.g. +19195551212)
BASE_URL           # The base URL for your application (e.g. https://myapp.ngrok.io)
LOG_LEVEL          # (optional) The logging level for the application (default: INFO)
LOCAL_PORT         # (optional) The local port for the application (default: 5000)
```

# Running the Application

This application is built using Python 3.13. You can use pip to install the required packages, or Docker Compose to run the application.

To install the required packages and run the application, you can use either of the following methods:

```sh
# Using Docker Compose 
docker compose up --build
```

```sh
# Using Python
python -m venv .venv
source .venv/bin/activate
cd app
pip install -r requirements.txt
python main.py
```

# Callback URLs

For a detailed introduction, check out our [Bandwidth Voice Webhooks](https://dev.bandwidth.com/docs/voice/programmable-voice/webhooks) page.

Below are the callback paths exposed by this application:
* `/health`
* `/webhooks/bandwidth/voice/initiate`
* `/webhooks/bandwidth/voice/status`

## Ngrok

A simple way to set up a local callback URL for testing is to use the free tool [ngrok](https://ngrok.com/).  
After you have downloaded and installed `ngrok` run the following command to open a public tunnel to your port (`$LOCAL_PORT`)

```sh
ngrok http $LOCAL_PORT
```

You can view your public URL at `http://127.0.0.1:4040` after ngrok is running.  You can also view the status of the tunnel and requests/responses here.
