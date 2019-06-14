# Page Troubleshooting

## Page hit tracking doesn't work

Page hits are being tracked by a tracking pixel. That is simply a 1 pixel GIF image in the source code of the Page source code. When a page is hit by a browser, it tries to load the images in it. The image load request is actually what Mautic needs to track the page hit action.

If the tracking doesn't work, check:

1. The tracking doesn't work for logged in Mautic administrators. This way statistics aren't skewed by Mautic administrators looking at the page result while editing a page. So make sure you are logged out of Mautic or use an incognito browser window while testing the tracking.
2. The tracking pixel isn't part of the page you want to track. Mautic can only track pages which have the tracking pixel in their source code.
3. The tracking pixel is not configured correctly. You can confirm this by looking at the dev tools of your browser. While looking on the page you wish to track, open the dev tools (press F12), go to the Network tab and reload the page. You'll see all the requests which were made. Filter those requests to images only and find the mtracking.gif image. Does it have status 200? If not, the path to your Mautic instance is probably incorrect.


[Info about the Tracking Pixel](./../contacts/contact_monitoring.html)
