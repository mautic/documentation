# Lead Monitoring
The act of monitoring the traffic and activity of leads can sometimes be somewhat technical and frustrating to understand. Mautic makes this monitoring simple and easy to configure.

### Website Monitoring

Monitoring all traffic on a website can be done by adding a single tracking pixel to the website.  It is important to note that traffic will not be monitored from logged-in Mautic users.  To check that the pixel is working, use an incognito or private browsing window.  Traffic will not be monitored until the session times out or the user logs out of Mautic.

```
http://yourdomain.com/mtracking.gif
```

To get the most out of the tracking pixel, it is recommended that you pass information of the current web page through the image URL.  Mautic currently supports `page_url`, `referrer`, `language`, and `page_title` (note that the use of `url` and `title` are deprecated due to conflicts with lead fields).  You can also pass information specific to your lead by setting Mautic lead field(s) to be publicly updatable. Note that values appended to the tracking pixel should be url encoded (%20 for spaces, %40 for @, etc).

An example tracking pixel may look like:

```
<img src="http://yourdomain.com/mtracking.gif?page_url=http%3a%2f%2fyourdomain.com%2fyour-product-page&page_title=Some%20Cool%20Product&email=user%40theirdomain.com" style="display: none;"  alt="mautic is open source marketing automation" />
```

If you are using a CMS, the easiest way is to let one of our plugins do this for you (see below).

Here are a couple code snippets that may help as well:

PHP

```
$d = urlencode(base64_encode(serialize(array(
    'page_url'   => $_SERVER['REQUEST_URI'],
    'page_title' => $pageTitle,    // Use your website's means of retrieving the title or manually insert it
    'email' => $loggedInUsersEmail // Use your website's means of user management to retrieve the email
))));

echo '<img src="http://your-mautic.com/mtracking.gif?d=' . $d . '" style="display: none;" />';
```

Javascript

```
<script>
var mauticUrl = 'http://your-mautic.com';
var src = mauticUrl + '/mtracking.gif?page_url=' + encodeURIComponent(window.location.href) + '&page_title=' + encodeURIComponent(document.title);
var img = document.createElement('img');
img.style.width  = '1px';
img.style.height  = '1px';
img.style.display = 'none';
img.src = src;
var body = document.getElementsByTagName('body')[0];
body.appendChild(img);
</script>
```

#### Available Plugins

Mautic makes this even easier by providing key integrations to many existing content management systems. You can download and use any of the following plugins to automatically add that tracking pixel to your website.

* [Joomla!](http://mautic.org/integration/joomla)
* [Drupal](http://mautic.org/integration/drupal)
* [WordPress](http://mautic.org/integration/wordpress)
* [Typo3](http://mautic.org/integration/typo3)
* [Concrete5](http://mautic.org/integration/concrete5)

These are just a few of the integrations already created by the Mautic community. More will be added in the future and developers are encouraged to submit their own integrations.

**Note:** It is important to note that you are not limited by these plugins and you can place the tracking pixel directly on any HTML page for website tracking.

### Mobile Monitoring

The essence of monitoring what happens in an App is similar to monitoring what happens on a website. Mautic contains the building blocks needed for native (or pseudo-native) and HTML5-wrapper based Apps, regardless of platform.

In short, use named screen views (e.g. main_screen) in your App as your page_url field in the tracker, and the lead's email as the unique identifier, see next section for detailed instructions.


#### Steps in Mautic

1. Make the email field publicly editable, this means that a call to the tracking GIF with the variable email will get properly recognized by Mautic.

2. Setup a form, which will be the access point of your campaign (e.g. a new lead email). Make this form as simple as you can, as you will be POST-ing to it from your App. The typical form URL you will POST to is

```
http://your_mautic/form/submit?formId=<form_id>
```

You can get the ID from the mautic URL as you view / edit the form in the Mautic interface (or in the forms tables, last column), and you can get the form fields by looking at the HTML of the 'Manual Copy' of the HTML in the forms editing page.


3. Define in your campaigns the screens you want to use as triggers (e.g. 'cart_screen' etc.). Mautic is not looking for a real URL in the form 'http://<url>' for page_url, any typical string would do. Like this:

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

#### In your App

A best-in-class approach is to have a class (say 'mautic') that handles all your tracking needs. For example, this sample method call would POST to the form with ID 3 - see previous section (note: for conciseness and ubiquity, these sample lines are written in JavaScript / ECMAScript-type language, use similar call in your mobile App language of choice).

```
mautic.addLead("myemail@somehwere.com",3)
```

And then, to track individual user activity in the App, this sample call would make an HTTP request to the tracker:

```
mautic.track("cart_screen", "myemail@somewhere.com")
```

Which is nothing more than an HTTP request to this GET-formatted URL (as also shown in previous section):

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

Important: Make sure in your App, that the above HTTP request is using a cookie (if possible, re-use the cookie from the mautic.addLead POST request prior) AND that you reuse this cookie from one request to the next. This how Mautic (and other tracking software) knows that it's really the same user. If you can't do this, you may run in the (unlikely but possible) case where you have multiple leads from the same IP address and Mautic will merge them all into a single lead as it can't tell who is who without a cookie.

### Other Online Monitoring

There are several other ways to monitor lead activity and attach points to those activities. Website monitoring is only one way to track leads. Other lead monitoring activities can consist of forum posts, chat room messages, mailing list discussion posts, GitHub/Bitbucket messages, code submissions, social media posts, and a myriad of other options.

### Troubleshooting

If the tracking doesn't work, take a look at [Page troubleshooting](pages/troubleshooting.html) or [Email troubleshooting](emails/troubleshooting.html)
