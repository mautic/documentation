# Focus

Focus allows you to engage users on your site through bars, modals, notifications and full page takeovers. These can be initiated at different times and with different actions such as exit intent.

Focus Items are listed under the Channels menu.

## Creating a Focus Item

When creating a focus item, you'll see that there is a place to enter a website. This is currently integrated into a service offered by mautic.com to generate a snapshot of the given website to use a preview when building the focus item. If the website is a very complex website - the snapshot may not work. Note that this feature may change in the future. 
 
![](media/step_1.png)

After entering the website, click the builder button top right. This is where the magic happens.

Notice that you should have a snapshot of the website. If not, you'll have the option to fetch it. Again note that some complex websites may not be snapshot-able.

![](media/step_2.png)
 
On the left, you'll see a button to switch between mobile and desktop views. A mobile snapshot is also attempted - it may not match your website exactly due to the snapshot process but it should at least give you the general look. On the right is the builder toolbar.   

![](media/step_3.png)

### Focus/Goal

The first step to building the focus item is to choose what the focus or goal is. There are three options:

1. Collect data - will use a Mautic form in the output as the content. Note that it should be a very simple form (One or or two inputs) as there is very little room to work with in some of the styles. But this is great for capturing emails for a newsletter signup.
2. Display a notice - information only and is great for announcements and the like.
3. Emphasize a link - great for landing pages with an event, sale, promotion, etc. It displays a button to click that will direct to the given link.

![](media/step_4.png)

Each focus/goal will have slightly different settings but all have a few in common:
  
1. Animate? - simply determine if  
1. When to engage - this determines when the focus is engaged based on visitor interaction. It can be immediate, on scroll, timed, or with an exit attempt. If `Visitor intends to leave` is chosen, an option appears that allows configuration if links within the site should trigger the engagement or not.
2. How often to engage - should the visitor be engaged every time, once per session, or during a period of time? 
3. Stop engaging after a conversion - once a user clicks the link or submits the form (not applicable for displaying a notice), enabling this option will no longer engage the visitor.

### Focus Style

![](media/step_5.png)

There are four styles supported - 

1. Bar - display a bar across the top or bottom of the page
2. Modal - a small modal window that appears centred on the page
3. Notification - these are like modals but smaller and slide in from the side.
4. Full page - also like a modal only it takes up the entire view.

Each style has its own settings such as position, size, sticky, etc.

#### Colors

![](media/step_6.png)

By default, Mautic will determine the top colors extracted from the snapshot. Four colors are currently supported for primary color, text color, button color, and button text color.
 
### Content

![](media/step_7.png)

Again this will vary based on the selected focus/goal and style is chosen. Some support a headline and a tagline while some support only a headline due to space constraints. If the goal is to collect data, a list of forms will be available to choose from. Remember that the form should be simple. 

## For advanced users

### Content mode

A new section called ‘content’ has been added to the builder for focus items that enables you to format content in basic, editor or html mode. This opens the door for even more creativity when engaging visitors to your site.

![](media/html-mode.png)

## Inserting focus into a website

![](media/step_8.png)

Inserting a focus item into a website is as simple as copying one line of code and inserting it into your page's source. After creating the focus item, view its details page where you can see engagement graphs and other detailed information. On the right, you'll see a  "Focus Installation" box that includes the line of code needed. Click on it, copy, then paste it into your website's source before the closing body tag if possible.

## Focus Items in Campaigns

Focus Items action depends on page visits. That means, **you have add it just after Visits a page decision**.

![](media/focus-campaign-action.gif)
