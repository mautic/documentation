# Email Troubleshooting

## Open email tracking doesn't work

Emails are being tracked by a tracking pixel. That is simply a 1 pixel GIF image in the source code of the Email message sent by Mautic. When the email is opened by an email client like Outlook, Thunderbird or GMail, it tries to load the images in it. The image load request is actually what Mautic needs to track the email open action.

Some Email clients has the image auto-loading disabled, and users have to click on a "Load Images" button to load images inside an email message. If the images aren't loaded for this reason or another, Mautic doesn't know about the open action. Therefore, email open tracking is not 100% accurate.
