# Email Troubleshooting

## Open email tracking doesn't get tracked

Emails are being tracked by a tracking pixel. This is simply a 1 pixel GIF image in the source code of email messages sent by Mautic. When an email is opened by an email client like Outlook, Thunderbird or GMail, the client tries to load the images in it. The image load request is what Mautic uses to track the email open action.

Some email clients have auto loading images disabled, and users have to click on a "Load Images" button to load images inside an email message. If the images aren't loaded for this reason or another, Mautic doesn't know about the open action. Therefore, email open tracking is not 100% accurate.

## Email link clicks are not getting tracked

Before an email is sent, Mautic replaces all links in the email with links back to Mautic including a unique key. If the lead clicks on such a link, the lead is redirected to Mautic. Mautic tracks the click action and redirects the lead to the original location. It's fast so the lead doesn't notice the additional redirect.

If the email click doesn't get tracked, make sure that:
1. Your Mautic server is on a public URL. Tracking doesn't work on a localhost.
2. Check if the link in the email has been replaced by the Mautic's tracking link. If not, report it to https://github.com/mautic/mautic/issues with all the details (Mautic version, PHP version, what the link URL is before sending, what it is after sending and so on).
