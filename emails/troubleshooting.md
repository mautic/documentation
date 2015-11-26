# Email Troubleshooting

## Open email tracking doesn't get tracked

Emails are being tracked by a tracking pixel. That is simply a 1 pixel GIF image in the source code of the Email message sent by Mautic. When the email is opened by an email client like Outlook, Thunderbird or GMail, it tries to load the images in it. The image load request is actually what Mautic needs to track the email open action.

Some Email clients has the image auto-loading disabled, and users have to click on a "Load Images" button to load images inside an email message. If the images aren't loaded for this reason or another, Mautic doesn't know about the open action. Therefore, email open tracking is not 100% accurate.

## Email link clicks doesn't get tracked

Before an email is sent, Mautic replaces all links in the email with links back to Mautic with a unique key. If someone clicks on such link, she gets redirected to Mautic. Mautic track the click action and redirects the lead to the original location. It's fast so the lead doesn't notice the additional redirect.

If the email click doesn't get tracked, make sure that:
1. Your Mautic server is on public URL. This tracking doesn't work on localhost.
2. The link tracking doesn't work for test emails, so make sure the email was send to an existing lead. Not by the *Send Example* link.
3. You've opened the link in a incognito browser. More about it in the [Pages troubleshooting](/pages/troubleshooting.html).
4. Check if the link in the email has been replaced by the Mautic's tracking link. If not, report it to [GitHub](https://github.com/mautic/mautic/issues) with all the details (Mautic version, PHP version, what the link URL is before send, what it is after send and so on).
