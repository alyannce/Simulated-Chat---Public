# Simulated Chat Study

## What the site does

The site guides participants through a scripted conversation with an unnamed chat partner. Participants imagine they are getting to know someone and choose the reply they would be most likely to send.

There are two versions of the chat partner's scripted responses:

- **Consistent positive feedback**
- **Fluctuating positive feedback**

The participant's assigned code determines which version they see. Their selected reply does not change the chat partner's next scripted message.

## What participants do

1. Enter their assigned participant code and answer a short question about their current mood.
2. Select **Check code**. The site verifies the participant code and determines the assigned chat condition.
3. Read **Before you begin**. The **Start chat** button becomes clickable after a five-second countdown.
4. Read the chat partner's messages and choose one of two replies at each turn.
5. After the fifth reply, choose whether to continue or end the conversation. Continuing shows one final turn; ending skips it.
6. Continue to the questionnaire selected for the assigned condition: the **Consistent** group receives [this Google Form](https://forms.gle/5ADpTyamzHN1uzCz9), and the **Fluctuating** group receives [this Google Form](https://forms.gle/WsqGGbB87PRuKuFZA).

The participant code field shows `e.g., A1B2C3` as a format example only; participants must enter the code assigned to them by the research team. The chat partner is shown with a generic blank profile icon and no displayed name. Chat messages appear in rounded bubbles with tails. Reply choices appear one second after each chat partner message.

## What information is collected

The study spreadsheet records:

- Participant code and assigned condition
- The participant's mood response
- Each conversation turn and the reply they selected
- The time each message appeared, the time they responded, and the calculated response time
- Whether they chose to continue or end after the fifth reply
- A session timestamp, used to group responses from the same chat

One row is stored per answered turn. The continue/end choice is recorded with the fifth-turn response. The site does not ask participants for their name, but responses are associated with their participant code. A free-text mood response could include personal information, so participants should only share what they are comfortable sharing.

### Spreadsheet fields

| Column | Description |
| --- | --- |
| `participant_id` | Assigned code entered by the participant |
| `condition` | `consistent` or `fluctuating` |
| `trial` | Turn number (1 to 6) |
| `partner_message` | Chat partner's scripted message |
| `selected_option_number` | Selected reply (1 or 2) |
| `selected_reply` | Text of the selected reply |
| `message_shown_at_ms` | Browser timestamp when the chat partner's message appeared |
| `choice_at` | ISO timestamp of the participant's reply |
| `response_latency_ms` | Time from message shown to reply |
| `session_started_at` | ISO timestamp when the session began |
| `mood_response` | Short answer entered before the chat |
| `conversation_decision` | `continue` or `end`, recorded on the Turn 5 row |

## Where the data goes

Responses are sent to the study Google Sheet managed by the research team:

- **Responses** contains study participant data.
- **Participants** contains assigned participant codes, their conditions, and session reservations.
- **TestingResponses** and **TestingSessions** are for researcher testing only and are kept separate from study responses.

The spreadsheet should only be accessible to authorized members of the research team. Follow the study's approved privacy, retention, and data-handling procedures.

## What Google Apps Script does

Google Apps Script is the small server-side program between the website and the Google Sheet. When a participant enters a code, it checks whether the code is assigned and which condition to show. When a participant submits a reply, it checks the session and condition, then writes the response to the appropriate sheet tab. It also prevents duplicate turn submissions and records the continue/end choice.

The website does not connect directly to the spreadsheet. Apps Script performs the spreadsheet operations using the research team's Google account. The spreadsheet stores the data; Apps Script handles the requests and study rules.

### Why this setup instead of a dedicated database?

For a small study or pilot, Google Sheets is convenient for a research team that already uses Google Workspace: it is straightforward to review and export, and it does not require a separate database service and its administration. Apps Script provides a lightweight way to connect the participant website to that spreadsheet.

Google Sheets is not a full database, and Apps Script is not a substitute for one. This setup has service quotas and is less suited to large numbers of simultaneous users, complex queries, strict access-control requirements, or sensitive data needing stronger safeguards. Participant codes act as access codes, not as strong authentication. If the study needs those capabilities or grows substantially, the team should consider a dedicated backend and database with appropriate authentication, access controls, backups, and monitoring.

## Participant codes and resuming a chat

Each real participant code is assigned a condition and can be used to start one study session. Participants can reload and resume that session in the same browser on the same device, using the site's **Resume saved chat** option. The browser stores session progress locally to support this. Clearing browser data or switching devices can remove access to the saved session; a researcher may need to assist.

The special code `TEST7785` is reserved for researcher testing. It alternates between the consistent and fluctuating conditions on new sessions, starting with consistent when there is no test-session history. Test records go to the testing tabs, not to **Responses**. Do not give this code to study participants or use it for real study data.

## Research team notes

- Provide each participant with their assigned code and the correct study information before they begin.
- Confirm both condition-specific questionnaire links are the intended final forms and accessible to participants.
- Review the Google Sheet to confirm responses are arriving.
- Use `TEST7785` for repeatable testing; avoid using real participant codes for tests.
- Contact the research team if a participant cannot resume their saved session or encounters an error.
