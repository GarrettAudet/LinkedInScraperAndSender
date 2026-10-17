# LinkedIn Profile Scraper

An experimental Manifest V3 Chrome extension that reads visible LinkedIn profile fields and uses Google Gemini to draft a personalized connection message.

## Current flow

1. On a LinkedIn profile page, the content script listens for F11.
2. After a 15-second delay, it reads the name, headline, About text, and work experience from page selectors.
3. The background flow requests a message from the Gemini API.
4. The generated message is displayed in an alert, with a clipboard-copy attempt.

The extension generates a draft; it does not automatically send a LinkedIn connection request.

## Structure

- `manifest.json`: extension permissions and entry points
- `content.js`: profile extraction and display
- `background.js`: message routing
- `generateMessage.js`: prompt construction and Gemini request
- `popup.html`: popup interface

## Configuration and limitations

The generator imports a local `config.js` with a `geminiApiKey` property. That file is not in the repository. Do not commit a real API key. Client-side extension credentials are accessible to the local extension environment and are unsuitable for a distributed production secret.

The prompt contains project-specific sender context and should be reviewed before use. Check the configured Gemini model endpoint before use. LinkedIn page selectors may change, and the F11 shortcut can conflict with browser fullscreen behavior.

## Privacy and responsible use

Profile fields are transmitted to Google Gemini when generation runs. Review the data and applicable service terms before use, obtain any required permission, and avoid bulk unsolicited outreach. Review every draft before sending it yourself.

