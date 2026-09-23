# Tudlo email templates

## `inquiry-reply.html`

HTML email to reply to people who send an inquiry. Same branding as the landing
page: services, a "Schedule a Zoom Meeting" CTA, and Telegram / WhatsApp /
KakaoTalk buttons.

### Before sending

All images (logos and button icons) are hosted PNGs in `emails/assets/`, served
from `https://tudlo-english.com/emails/assets/`. Gmail/Outlook block base64
images and inline SVG, so keep them as hosted `<img>` tags.

- After changing anything in `emails/`, commit and push — the send script
  fetches the template from GitHub Pages, so changes only show up once Pages
  has redeployed.
- `{{first_name}}` — leave it; the send script fills it in per client.

### Sending

Don't paste the HTML into the Gmail compose box — it sends blank. Use one of:

- **`apps-script/Code.gs`** — Google Apps Script. `sendTudloReply()` for one
  client, `sendBatch()` to send to every unsent row of a Google Sheet
  (`name`, `email`, `sent` columns). Set `TEMPLATE_URL` to the hosted
  `inquiry-reply.html`.
- A dedicated email service (Brevo, Mailchimp, MailerSend, …) — paste the HTML,
  upload the logos to its image library, send.

Gmail cap: ~500 recipients/day (consumer), 2,000 (Workspace).
