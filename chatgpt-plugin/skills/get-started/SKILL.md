---
name: get-started
description: Set up a new Roar AI account and show what Roar AI can do. Use when the person sets up the Roar AI plugin, asks to set up their Roar AI account, or asks how to get started with Roar AI.
---

# Get started with Roar AI

Help the person set up their Roar AI account in two short answers, then get them to a first result.

## 1. Ask for two names

In one short message, ask for their own name and their company's name, and say that if it is just them, their name is enough. Ask nothing else. Use only what they tell you: never guess a name or take one from anywhere else.

## 2. Save them

Call `set_up_account` with `fullName`, and with `company` unless it is just them.

- If it succeeds, confirm in one line: "You're set up, <first name>."
- If it says the account is already set up, say so in one line and carry on. Do not try again or try another way to rename it.

## 3. Show what they can do

Show the groups and example requests from the tool's `next` reply, as they are. If the tool gave none, show this:

**Build an app on Roar AI**
- "Build a customer support chat for my website on Roar AI"
- "Build an app that summarises my customer emails on Roar AI"
- "Build a tool that writes product descriptions on Roar AI"

**Already have an app?**
- "Deploy my app and give me the live link"

Then ask: "What would you like to do first?"

## 4. Do the first task

When they pick one, do it with the Roar AI tools.

- **Building an app:** agree in a few lines what the app does, then write it with them. The app reads its Roar AI key from `ROAR_API_KEY` and the AI endpoint from `ROAR_BASE_URL`, which is OpenAI-compatible. Roar AI gives every deployed app its own key, so never put a key in the code or the chat. Put the app online with `deploy_app_from_files`, which takes the files you wrote straight from this chat, so no GitHub repository is needed. Share the live link from `get_deploy_status`. When they ask for a change later, send only the files that changed with `update_app_files`.
- **Deploying an app they already have:** ask where it is. If it is on their computer, ask them to attach its files or a .zip here, then send them with `deploy_app_from_files`. If it is in a GitHub repository connected to Roar AI, deploy it with `deploy_app`. Then share the live link.

## Keep it simple

- Short messages, plain words. The person may not be a developer.
- No prices, credit or offers.
- Do not ask what they plan to use Roar AI for, or anything about their business, beyond the two names.
