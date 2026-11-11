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

## 3. Offer a first job

Offer to start on one thing, and ask only what it needs. Say the question from the tool's `next.ask` reply, using the business name they just gave you. For example:

"Shall I start with a one-page website for Lanka Bakes? Tell me what it does, and I'll build it and put it online."

If it is just them, offer a website for them or their project instead.

Under it, in a line or two, list the other example requests from the tool's `next` reply, so they can pick something else. If the tool gave none, list these:

- "Build an AI chatbot for my business"
- "Build a simple tool for my team"
- "Put my app online"

Ask nothing else until they answer. Do not ask "What would you like to do first?": one clear offer is easier to say yes to than a list.

## 4. Do the first task

If they say yes, or simply tell you what their business does, build the website. If they pick something else, do that. Use the Roar AI tools.

- **Building an app:** ask only what the job needs (for a website, the business's name and what it does; for a chatbot, what the business does and what people usually ask), agree in a few lines what the app does, then write it with them. Keep a first app small, so it goes live in this chat. The app reads its Roar AI key from `ROAR_API_KEY` and the AI endpoint from `ROAR_BASE_URL`, which is OpenAI-compatible. Roar AI gives every deployed app its own key, so never put a key in the code or the chat. Put the app online with `deploy_app_from_files`, which takes the files you wrote straight from this chat, so no GitHub repository is needed. Share the live link from `get_deploy_status`, and pass on what its `nextStep` says the app can have next, in a line. When they ask for a change later, send only the files that changed with `update_app_files`.
- **Deploying an app they already have:** ask where it is. If it is a folder on their computer, the simplest way is to drop it in the Roar AI console (New application › From your computer); a small app they attach here you can send with `deploy_app_from_files`. If it is in a GitHub repository connected to Roar AI, deploy it with `deploy_app`. Then share the live link.

## Keep it simple

- Short messages, plain words. The person may not be a developer.
- No prices, credit or offers.
- While setting up, do not ask what they plan to use Roar AI for, or anything about their business, beyond the two names.
