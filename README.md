# Simulated Chat Study

## What the site does

The site guides participants through a scripted conversation with Alex. Participants imagine they are getting to know someone and choose the reply they would be most likely to send.

There are two versions of Alex's scripted responses:

- **Consistent positive feedback**
- **Fluctuating positive feedback**

The participant's assigned code determines which version they see. Their selected reply does not change Alex's next scripted message.

## What participants do

1. Enter their assigned participant code.
2. Answer a short question about their current mood.
3. Read Alex's messages and choose one of two replies at each turn.
4. After the fifth reply, choose whether to continue or end the conversation. Continuing shows one final turn; ending skips it.
5. Continue to the questionnaire using the link provided by the research team.

## What information is collected

The study spreadsheet records:

- Participant code and assigned condition
- The participant's mood response
- Each conversation turn and the reply they selected
- The time each message appeared, the time they responded, and the calculated response time
- Whether they chose to continue or end after the fifth reply
- A session timestamp, used to group responses from the same chat

One row is stored per answered turn. The continue/end choice is recorded with the fifth-turn response. The site does not ask participants for their name, but responses are associated with their participant code. A free-text mood response could include personal information, so participants should only share what they are comfortable sharing.

## Where the data goes

Responses are sent to the study Google Sheet managed by the research team:

- **Responses** contains study participant data.
- **Participants** contains assigned participant codes, their conditions, and session reservations.
- **TestingResponses** and **TestingSessions** are for researcher testing only and are kept separate from study responses.

The spreadsheet should only be accessible to authorized members of the research team. Follow the study's approved privacy, retention, and data-handling procedures.

## Participant codes and resuming a chat

Each real participant code is assigned a condition and can be used to start one study session. Participants can reload and resume that session in the same browser on the same device, using the site's **Resume saved chat** option. The browser stores session progress locally to support this. Clearing browser data or switching devices can remove access to the saved session; a researcher may need to assist.

The special code `TEST7785` is reserved for researcher testing. It alternates between the consistent and fluctuating conditions on new sessions, starting with consistent when there is no test-session history. Test records go to the testing tabs, not to **Responses**. Do not give this code to study participants or use it for real study data.

## Research team notes

- Provide each participant with their assigned code and the correct study information before they begin.
- Confirm the final questionnaire link is available to participants.
- Review the Google Sheet to confirm responses are arriving.
- Use `TEST7785` for repeatable testing; avoid using real participant codes for tests.
- Contact the research team if a participant cannot resume their saved session or encounters an error.
