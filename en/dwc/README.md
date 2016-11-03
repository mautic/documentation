# Dynamic Web Content

Mautic 2.0 introduced the ability to embed content on a web page dynamically for both anonymous visitors and known contacts.

There are several steps involved in setting this up.

##Setup
###Add the default content.
![](/dwc/media/dwc-default.jpg)

###Add alternative content if desired.
You can set up as many items as you need.  The default will be delivered via the "Request Dynamic Content" decision in a campaign.  If you want to push something different based on a set of criteria, you create those here and deliver them via a "Push Dynamic Content" action.

###Add the dynamic content pull request in a campaign.  
The key to this step is naming the "slot".  This can be anything you want as long as it's unique across your dynamica content campaigns.  The pull request is processed and determines if the person on the landing page is a known contact.
![](/dwc/media/dwc-pull-request.jpg)

###Add the push request in the campaign.  
If you want to serve up different information based on certain criteria, you can use a push request.  
1.  If the person is known, they receive the content from the pull request.  
2.  If they meet the criteria (in the example below - if they are from Canada), a different set of content can be delivered to the browser.  
3.  If they are unknown, they will see the information embedded in the dynamic web content div from the page (see below).
![](/dwc/media/dwc-push.jpg)

###Finally, include the dynamic web content shortcode in your web page.  
```
<div class="mautic-slot" data-slot-name="dwc">Text in the html - 
this shows up if the visitor is not known</div>
```
Note the data-slot-name matches the slot name in the campaign.

Watch a video tutorial:  (https://www.youtube.com/watch?v=eChzJm5yBUk)

## Translations

Dynamic web content supports translated content. When creating/editing a dynamic web content item, there are the options to set a language and select a translation parent. By selecting a translation parent, the current item is then considered to be a translation in the selected language of that parent item. 
