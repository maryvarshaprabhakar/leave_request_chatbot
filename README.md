# Leave Request Chatbot (Dialogflow)

A conversational chatbot that lets an employee apply for leave by chatting instead of filling in a form. It is built with Google Dialogflow and uses **Natural Language Processing (NLP)** to understand what the user types, such as the leave type and dates in different formats (`08-Jan`, `2027-03-20`, `24th Oct`).

The user picks a leave type, chooses the dates, sets first half or second half for the start and end days, reviews a summary, and confirms. The bot then replies with a tracking number.

I built this as a small personal project. I previously worked on a leave-application bot in India, and I wanted to rebuild a simple, clean version of that idea from scratch for my portfolio.

---

## Key Concepts Used

- **NLP (Natural Language Processing):** the bot understands free-text messages instead of fixed commands
- **Intent recognition:** detects that the user wants to apply for leave
- **Entities:** extract the leave type and dates from the user's message
- **Parameters and prompts:** the bot asks again until all required details are collected
- **Conversational flow design:** a multi-step flow with a review and confirmation step

---

## What It Does

- Asks which type of leave the user wants (Casual, Sick or Earned)
- Accepts the start date as a quick option (Today / Tomorrow) or typed in
- Asks for the end date, with a "Same day" shortcut for one-day leave
- Handles half days: first half or second half for the start date and the end date
- Calculates the total duration (for example, 3.0 days)
- Shows a review summary and asks for confirmation before submitting
- Returns a tracking number once the request is submitted

---

## Example Conversation (Casual Leave)

| Step | Who | Message |
|------|-----|---------|
| 1 | User | I want to apply leave |
| 2 | Bot | Sure! I can help you submit a leave request. Which type of leave would you like to apply for? (Casual Leave / Sick Leave / Earned Leave) |
| 3 | User | Casual Leave |
| 4 | Bot | Got it, casual leave . When would you like to start your leave? You can choose a quick option below or type a date (e.g., YYYY-MM-DD or 24th Oct) (Today / Tomorrow) |
| 5 | User | 12-Jan |
| 6 | Bot | Great. And what is the last day of your leave? (Same day/ Select end date) |
| 7 | User | 14-Jan |
| 8 | Bot |Noted. To calculate the exact duration, please specify the half-day options: Start Date: First half or second half End Date: First half or second half
| 9 | User | First half for start, second half for end |
| 10 | Bot | Perfect. Please review your leave application before submission: Type: Casual Leave Duration: 12 Jan – 14 Jan (3.0 Days) Would you like to confirm and submit this request? (Yes / No) |
| 11 | User | Yes |
| 12 | Bot | Success! Your leave request has been submitted to your manager for approval. Tracking Number: LR-93581 You can use this tracking number anytime to check your status.|

---

## Screenshots

![Leave type selection](screenshots/01-leave-type.png)

![Date selection](screenshots/02-dates.png)

![Half day selection](screenshots/03-half-day.png)

![Review and confirm](screenshots/04-confirm.png)

![Submission success](screenshots/05-success.png)
<img width="766" height="1139" alt="Screenshot (192)" src="https://github.com/user-attachments/assets/8a0b61b0-b26d-4eda-8c03-ed440cab136f" />

---

## Leave Types

| Leave Type | Status | Notes |
|------------|--------|-------|
| Casual Leave | Built | Full flow: dates, half days, review, confirmation |
| Sick Leave | Planned | Same flow, plus a question about a medical certificate |
| Earned Leave | Planned | Same flow, plus a leave balance check |

For this version I focused on getting one flow working from start to finish (Casual Leave). Sick Leave and Earned Leave follow the same structure.

---

## Built With

- **Google Dialogflow ES** for intents, entities, parameters and the conversation flow
- **Quick replies / custom payload** for the clickable options (leave types, Today/Tomorrow, Yes/No)

---

## How It Works

1. An `apply_leave` intent starts the conversation.
2. The bot collects the leave type, start date, end date and half-day choices as parameters, and asks again if something is missing.
3. A confirmation step shows a summary of everything the user entered.
4. On "Yes", the bot sends the success message with the tracking number. On "No", the request is cancelled.

---

## Conversation Flow & UI Demonstration

To showcase the end-to-end functionality of the agent, I have attached screenshots from the Dialogflow Messenger interface below. These demonstrate the complete user interaction flow, including multi-turn entity extraction, half-day state tracking, dynamic duration calculations, and request tracking ID confirmations.

---

## Known Limitations

- This is a prototype and is not connected to a real HR system or database.
- The tracking number in the example is a sample value.
