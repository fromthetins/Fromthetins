# Connect a replacement email backend

Recipient: **teachers@fromthetins.in**

## Current status

The previous provider has been removed at the owner’s request. The form currently prepares a copyable enquiry only. Its button and status text explicitly say that nothing is sent. The direct email link still works through the visitor’s email app.

Automatic sending is **not enabled** until a replacement endpoint or deployed backend is supplied and tested. The assistant has not changed the already-published website; upload the updated files to remove the old connection there too.

## Recommended option: a public Formspree endpoint

1. Create a form in your account at https://formspree.io/.
2. Set its destination to **teachers@fromthetins.in** and complete any recipient-verification steps requested by the service.
3. Copy the form’s public endpoint URL, using the structure `https://formspree.io/f/<your-form-id>`.
4. Share that public endpoint with the assistant so it can connect the Send button, provider disclosure, response handling and native POST fallback.
5. Deploy the resulting update, submit one test enquiry, and check the recipient inbox before relying on the form.

The public endpoint is intended for a browser-facing form. Do not share an email password or private API key. No account or form has been created for you by the assistant.

## Alternative: your own backend

Provide a deployed HTTPS endpoint that accepts enquiry submissions and sends mail server-side. SMTP credentials or email-service API secrets must remain in server-side environment variables, never in the single-file HTML or public repository. A static GitHub Pages website cannot run that backend itself.

## Offline viewing

The self-contained HTML remains readable offline. Automatic email sending, once configured, will require internet access. Arena’s file viewer blocks outgoing network requests; test delivery on the deployed public HTTPS website.
