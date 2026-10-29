# Enable automatic email enquiries

Recipient: **teachers@fromthetins.in**
Provider: **FormSubmit**, chosen by the site owner.

## One-time activation

1. Upload the updated GitHub Pages package to the repository’s publishing root, preserving the `assets/` folder. The existing public URL remains https://fromthetins.github.io/Fromthetins/.
2. Open the published HTTPS page and submit one test enquiry using an email address you control. The site sends submissions through FormSubmit; it does not open the visitor’s email app.
3. Check **teachers@fromthetins.in**, including its spam folder, for the FormSubmit activation email. Follow its confirmation link. Make sure the mailbox itself can receive mail.
4. After activation, submit a fresh test enquiry and verify it arrives in that inbox. Do not assume the first, pre-activation enquiry was delivered.
5. If activation does not appear, check the provider’s instructions at https://formsubmit.co/. No email password or secret key belongs in the public HTML.

**Status at handoff:** the integration is configured and its success/error/offline flows have been tested with mocked provider responses. No real test submission, activation email, mailbox verification or inbox-delivery test was performed by the assistant. Deployment and activation remain the owner’s steps.

## How it works

- JavaScript: JSON POST to `https://formsubmit.co/ajax/teachers@fromthetins.in`.
- Without JavaScript: native POST to `https://formsubmit.co/teachers@fromthetins.in`, which opens the provider’s hosted flow.
- The visitor’s name, email, selected interest and message are shared with FormSubmit for delivery. This is disclosed beside the Send button.
- No SMTP credentials are embedded and there is no locally hosted email backend.
- In-flight duplicate submissions are blocked. Requests time out after 15 seconds without automatic retries.
- A positive API response is a submission acknowledgment, not an inbox-delivery receipt. Timeout errors may occur after a request reached the provider; avoid blindly resending.
- The copyable enquiry and direct email link remain available as fallbacks. No enquiry is persisted in browser storage.

## Offline files and previews

All visual assets remain embedded in `The-Tins.html`; the page can be read offline. Sending requires internet access and provider acceptance of the page’s origin. Use the published HTTPS site for real submissions. Local `file://` pages may be rejected by the provider, and Arena’s file viewer blocks outbound network requests. The live preview can exercise the request flow, but the public website is the final deployment to test.
