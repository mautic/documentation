# Campaign Troubleshooting

## Page visits are not recognized

There can be a few reasons for this:

1) Make sure that you are not testing the page visit while logged into Mautic. Mautic ignores user generated activity so use an anonymous session, another browser, or logout of Mautic.

2) Ensure the contact getting tracked is in the campaign. The easy way to test this is to review the time line of the contact for the page hit.

3) Campaigns are executed sequentially and will not repeat per contact. If the contact has already visited the page while part of the campaign and triggered the Visits a Page decision, subsequent visits will not re-trigger the actions associated with the decision.

4) Ensure that the URL in the campaign action either matches _exactly_ the URL visited or use a wildcard (note that the <a href="https://en.wikipedia.org/wiki/Uniform_Resource_Locator" target="_blank">a URL can include the schema, host/domain, path, query parameters, and/or fragment</a>).

For example, if you have a URL of `http://example.com` and the page hit registers as `http://example.com/index.php?foo=bar`, the campaign decision will not be triggered. However, if you use `http://example.com*` as the URL, it'll match and thus trigger.

Another example is if you want to associate different page hits with specific campaigns. Let's say you have Campaign A and Campaign B. You want to use the same base URL and path for both campaigns but differentiate with a query parameter.  For Campaign A, you can define a Visits a Page decision with `http://example.com/my-page?utm_campaign=A*` and for Campaign B, `http://example.com/my-page?utm_campaign=B*`. Now a contact will only trigger the specific campaign desired. If the goal is to trigger both campaigns regardless of the query parameters, use `http://example.com/my-page*`.
