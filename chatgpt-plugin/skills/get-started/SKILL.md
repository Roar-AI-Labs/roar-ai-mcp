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

**Give your app AI**
- "Add an AI chat assistant to my website"
- "Add AI that summarises customer emails in my app"
- "Add AI that writes product descriptions in my app"

**Get your app online**
- "Deploy my app and give me the live link"

Then ask: "What would you like to do first?"

## 4. Do the first task

When they pick one, do it with the Roar AI tools.

- **Giving an app AI:** call `create_key` with a monthly spending limit the person agrees to. The key is never shown in the chat: the reply holds a one-time setup code. Tell them to paste the code into the coding assistant that works on their app (such as Codex, Claude Code or Cursor), which saves the key and adds the code. The setup code expires after a short time, so suggest doing it straight away.
- **Putting an app online:** ask which GitHub repository it is in, then deploy it and share the live link.

## Keep it simple

- Short messages, plain words. The person may not be a developer.
- No prices, credit or offers.
- Do not ask what they plan to use Roar AI for, or anything about their business, beyond the two names.
