---
name: build-and-change-apps
description: Build an app with the person and put it online with Roar AI, change an app that is already online, give it AI, or limit what it spends. Use when the person asks to make, deploy, update or fix an app or website on Roar AI.
---

# Build and change apps on Roar AI

Roar AI puts an app online from the files written in this chat and runs it. No GitHub account, server or ZIP file is needed.

## Build a new app

1. Ask only what the job needs. For a website: what the business is called and what it does. For an AI tool: what it should do, plus whatever that job needs (for a chatbot, what people usually ask).
2. Agree in a few lines what the app does, then write it. Keep a first app small.
3. Put it online with `deploy_app_from_files`. The answer gives the app's `appId`: keep it for every later step.
4. Call `get_deploy_status` with `waitSeconds` until it is live, then share the link. Pass on in one line what its `nextStep` says the app can have next.

## Change an app that is already online

Never ask the person to connect GitHub or upload a ZIP for an app that was deployed from files. Its files are on Roar AI.

1. Find the app with `list_apps` if you do not have its `appId`.
2. If its files are not in this chat, call `list_app_files`, then `read_app_file` for each file you will change.
3. Send only the files that changed with `update_app_files`. Every other file stays as it is.
4. Call `get_deploy_status` with `waitSeconds`, then share the link.

Use `update_app_files` for a change. `deploy_app_from_files` always makes a new app with a new address.

If a change is refused because a deploy is already running, call `get_deploy_status` with `waitSeconds` until it finishes, then send the change again.

An app that deploys from a GitHub repository is changed by pushing to that repository.

## Give an app AI

Every app on Roar AI already has its own key. The app reads it from `ROAR_API_KEY`, and the endpoint from `ROAR_BASE_URL`, which is OpenAI-compatible. `list_models` gives the model names.

- Do not create a key for an app hosted on Roar AI.
- Never put a key in the code or in the chat.
- Call the models from the app's server code, not from the browser.
- Use a low-cost model unless the person asks for another, and stream replies as they are written.
- Make it work well on a phone.

A website can have a small chat assistant that answers visitors' questions from the business's details. Offer it once a website is live, and add it if the person wants it.

## Add a picture

- If the person attached a logo or photo, put it in the app with `add_app_image`. Pass the attachment itself as `image`, never as text or base64.
- If they have no logo, `generate_image` with `saveAs` (for example `images/logo.png`) makes one and saves it in the app's files.

Both save the picture without deploying it, and return an `uploadId`. Refer to the picture from the app's pages, then send the changed pages with that `uploadId`: `update_app_files` for an app that is already online, `deploy_app_from_files` for a new one.

If the picture cannot be read, ask the person to attach it again from chatgpt.com or the ChatGPT desktop app.

## Limit what an app spends on AI

Use `set_app_ai_budget` with the app's `appId` and a monthly amount in USD. The app's AI calls stop when the month's spend reaches it, and start again the next month. `get_app_ai_budget` shows the current limit.

You can set a first limit or lower one. Raising or removing a limit is done by a person in the Roar AI console, under API keys.

Do not create a new key to carry a limit: the app would not use it.

## When a deploy fails

`get_deploy_status` says what went wrong. `get_build_logs` has the detail. Fix the files and send them with `update_app_files`.

## Keep it simple

- Short messages, plain words.
- No prices, credit or offers.
- Share the live link whenever the app changes.
