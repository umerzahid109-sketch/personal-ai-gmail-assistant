
# Personal AI Gmail Assistant

An AI-powered Gmail automation project that classifies emails, applies Gmail labels, and sends a daily email digest using Google Apps Script and the OpenRouter API.

## Features

- **AI email classification:** Categorizes recent emails into interviews, job applications, action-required messages, university emails, personal emails, receipts, newsletters, and other messages.
- **Automatic Gmail labeling:** Applies category labels to help organize the inbox.
- **Priority assessment:** Assigns High, Medium, or Low priority to classified emails.
- **Action detection:** Identifies whether an email requires a response or another action.
- **Deadline extraction:** Extracts stated deadlines without intentionally inventing dates.
- **Daily email digest:** Sends a structured summary of recent inbox messages.
- **Security alert detection:** Separates common account security notifications.
- **Keyword-based scanning:** Provides an additional way to identify important messages.
- **Scheduled automation:** Uses a time-driven Google Apps Script trigger to send the digest.
- **Privacy-conscious design:** Keeps the OpenRouter API key in Script Properties rather than hardcoding it.

## Technology Stack

- Google Apps Script
- JavaScript
- Gmail Service
- OpenRouter API
- NVIDIA Nemotron 3.5 Lightning (free model endpoint)
- JSON
- Google Apps Script time-driven triggers

## How It Works

1. The script searches recent inbox messages.
2. Selected emails are sent to the configured AI model for classification.
3. The model returns structured information, including category, priority, summary, action requirement, and deadline.
4. Gmail labels are applied to successfully classified threads.
5. A processed marker helps prevent repeated classification.
6. A separate digest function organizes recent inbox messages into readable sections.
7. A scheduled trigger sends the digest automatically.

The digest currently uses Gmail labels and subject-based rules. It does not generate an AI-written summary for every email.

## Gmail Labels

The project uses the following labels:

- `AI/Interviews`
- `AI/Action Required`
- `AI/Job Applications`
- `AI/University`
- `AI/Personal`
- `AI/Receipts`
- `AI/Newsletters`
- `AI/Review`
- `AI/Processed`

## Setup Instructions

### 1. Create a Google Apps Script project

1. Open [Google Apps Script](https://script.google.com/).
2. Create a new project.
3. Copy the contents of `Code.gs` into the Apps Script editor.

### 2. Configure the API key

1. Create an API key through your OpenRouter account.
2. Open your Apps Script project settings.
3. Find **Script Properties**.
4. Add the property `OPENROUTER_API_KEY`.
5. Store your API key as its value.

Never commit API keys, passwords, or tokens to GitHub.

### 3. Authorize Gmail access

Run the required setup function and follow Google's authorization prompts. Review the permissions requested before approving them.

### 4. Set up Gmail labels

Run:

`setupGmailLabels()`

### 5. Test the connection

Run:

`testOpenRouterConnection()`

Then use:

`testEmailClassification()`

Check the execution logs for the results.

### 6. Configure the automation

Run `classifyRecentEmailsWithAI()` when you want to classify eligible recent inbox threads.

Run `sendDailyEmailDigest()` to test digest delivery.

To send the digest automatically, configure a time-driven trigger in Apps Script. Set the project time zone to your intended local time zone.

## Available Functions

| Function | Purpose |
|---|---|
| `setupGmailLabels()` | Creates missing Gmail labels |
| `scanImportantEmails()` | Scans recent messages using keyword rules |
| `testOpenRouterConnection()` | Tests connectivity to OpenRouter |
| `testEmailClassification()` | Tests AI classification with a sample email |
| `classifyRecentEmailsWithAI()` | Classifies eligible inbox threads and applies labels |
| `sendDailyEmailDigest()` | Sends the daily email digest |

## Security and Limitations

- Keep the API key in Script Properties.
- Never publish real emails, personal information, access tokens, or API keys.
- Review Google's requested permissions before authorizing the script.
- AI classifications can be incorrect or incomplete.
- Free model availability, response quality, and rate limits may vary.
- The digest uses label and subject-based rules, so some emails may be categorized incorrectly.
- Always verify important deadlines, interview details, and security alerts directly in Gmail.

The project is designed to organize emails and send a digest. Its current functions do not automatically delete emails, archive them, or send replies.

## Future Improvements

- Improve interview and action-required detection.
- Add configurable email priority filters.
- Improve error handling and retry logic.
- Add more detailed logging and monitoring.
- Support customizable digest categories.
- Explore AI-generated summaries for selected emails.

## Author

**Muhammad Umer Zahid**

Software Engineering Graduate | Aspiring AI Engineer
