# Dynamic Web Content

Mautic 2.0 introduced the ability to embed content on a web page dynamically for both anonymous visitors and known contacts.

There are several steps involved in setting this up.

##Setup
###Add the default content.
![](/dwc/media/dwc-default.jpg)

###Add alternative content if desired.

###Add the dynamic content pull request in a campaign.  
The key to this step is naming the "slot".  This can be anything you want as long as it's unique across your dynamica content campaigns.  The pull request is processed and determines if the person on the landing page is a known contact.
![](/dwc/media/dwc-pull-request.jpg)

###Add the push request in the campaign.  
Once the pull request is processed and Mautic determines if the visitor is a known contact, then the push request is initiated.  If the person is known, you can send them one set of content.  If they are unknown, they will see the information as seen below.
![](/dwc/media/dwc-campaign.jpg)

###Finally, include the dynamic web content shortcode in your web page.  
```
<div class="mautic-slot" data-slot-name="dwc">Text in the html - 
this shows up if the visitor is not known</div>
```
Note the data-slot-name matches the slot name in the campaign.

Watch a video tutorial:  (https://www.youtube.com/watch?v=eChzJm5yBUk)
