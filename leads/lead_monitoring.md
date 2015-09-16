# Lead Monitoring
The act of monitoring the traffic and activity of leads can sometimes be somewhat technical and frustrating to understand. Mautic makes this monitoring simple and easy to configure.

### Website Monitoring

Monitoring all traffic on a website can be done by adding a single tracking pixel to the website.

```
http://yourdomain.com/mtracking.gif
```

To get the most out of the tracking pixel, it is recommended that you pass information of the current web page through the image URL.  Mautic currently supports url, referrer, language, and title.  You can also pass information specific to your lead by setting Mautic lead field(s) to be publicly updatable. Note that values appended to the tracking pixel should be url encoded (%20 for spaces, %40 for @, etc).

An example tracking pixel may look like:

```
<img src="http://yourdomain.com/mtracking.gif?url=http%3a%2f%2fyourdomain.com%2fyour-product-page&title=Some%20Cool%20Product&email=user%40theirdomain.com" style="display: none;"  alt="mautic is open source marketing automation" />
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

### Other Online Monitoring

There are several other ways to monitor lead activity and attach points to those activities. Website monitoring is only one way to track leads. Other lead monitoring activities can consist of forum posts, chat room messages, mailing list discussion posts, GitHub/Bitbucket messages, code submissions, social media posts, and a myriad of other options.
