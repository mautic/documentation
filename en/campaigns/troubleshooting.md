# Campaign Troubleshooting

## Page visits are not recognized

There can be a few reasons for this:

1. Make sure that you are not testing teh page visit while logged into Mautic. Mautic ignores user generated activity so use an anonymous session, another browser, or logout of Mautic.
2. Ensure the contact getting tracked is the in the campaign. The easy way to test this is to review the time line of the contact for the page hit.
3. Campaigns are executed sequentially and will not repeat per contact. If the contact has already visited the page while part of the campaign and triggered the Visits a Page decision, subsequent visits will not re-trigger the actions associated with the decision.
4. Ensure that the URL in the campaign action either matches _exactly_ the URL visited or use a wildcard. For example, if you have a URL of `http://domain.com` and the page hit registers as `http://domain.com/index.php?foo=bar`, the campaign decision will not be triggered. However, if you use `http://domain.com*` as the URL, it'll match and thus trigger. This is so you can associate different page hits with specific campaigns.

For example, let's say we have Campaign A and Campaign B. I want to use the same base URL for both campaigns but differentiate with a query parameter.  So for Campaign A, we can define a Visits a Page decision with `http://domain.com/my-page?utm_campaign=A*` and for Campaign B, `http://domain.com/my-page?utm_campaign=A*`. Now a contact will only trigger the specific campaign desired. If the goal is to trigger both campaigns regardless of the query parameters, we would use `http://domain.com/my-page*`.