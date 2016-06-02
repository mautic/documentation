# Points Troubleshooting

## Page visits are not recognized

There can be a few reasons for this:

1. Make sure that you are not testing teh page visit while logged into Mautic. Mautic ignores user generated activity so use an anonymous session, another browser, or logout of Mautic.
3. At this time, point actions are tracked once per contact. This means that subsequent visits will not re-trigger the action if already triggered once.
4. Ensure that the URL defined either matches _exactly_ the URL visited or use a wildcard. For example, if you have a URL of `http://domain.com` and the page hit registers as `http://domain.com/index.php?foo=bar`, the action will not be recognized. However, if you use `http://domain.com*` as the URL, it'll match and thus trigger.