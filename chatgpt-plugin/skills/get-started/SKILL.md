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

- **Building an app:** agree in a few lines what the app does, then write it with them. Give it AI with `create_key`, using a monthly spending limit the person agrees to. The key is never shown in the chat: the reply holds a one-time setup code, which expires after a short time. Put the app online with `deploy_app` and share the live link.
- **If you cannot put the code in a GitHub repository yourself**, say so plainly: `deploy_app` needs one. Suggest finishing the build in a coding assistant with Roar AI connected, such as Codex, Claude Code or Cursor, and give them the prompt to paste there. It can redeem the setup code to save the key.
- **Deploying an app they already have:** ask which GitHub repository it is in, then deploy it and share the live link.

## Keep it simple

- Short messages, plain words. The person may not be a developer.
- No prices, credit or offers.
- Do not ask what they plan to use Roar AI for, or anything about their business, beyond the two names.
