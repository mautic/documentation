# Emails

Emails can be created to be used within campaigns and other list activities. Emails provide a means for direct interaction with potential customers, clients, and leads.

### Email Formats

Emails can be created in both full HTML as well as basic text format to be delivered as necessary to leads. This is an important part of creating a strong relationship with leads by providing relevant information in the correct format.

### Email Delivery

Emails are delivered using the method defined by the system administrator. If you are the system administrator for your company, then you will need to add the email protocol for your company to use. Mautic integrates with any email service provider which offers SMTP mail servers as well as several distinct services such as Mandrill, Sendgrid, and Amazon SES.

The system can either send emails immediately or queue them to be processed in batches by a cron job.

#### Immediate Delivery ####

This is the default means of delivery. Mautic sends the email as soon as it is instructed to by the triggering action. If you expect a large number of emails to be sent, then utilizing the queue is recommended. Sending email immediately may slow the response time of Mautic if using a remote mail service since as Mautic has to establish a connection with that service before sending the mail. Also attempting to send large batches of emails at once may hit your server's PHP limits or email limits if on a shared host. 
 
#### Queued Delivery ####

This is recommended if you plan to send a significant number of emails. Mautic will store the email in the configured spool directory until the command to process the queue is executed. Set up a cron job at the desired interval to run the command:

```
php /path/to/mautic mautic:email:process --env=prod
```

Some hosts may have limits on the number of emails that can sent during a specified timeframe and/or limit the execution time of a script. If that's the case for you, or if you just want to moderate batch processing, you can configure batch numbers and time limits in Mautic's Configuration. 

 
### Email Fields

You have access to any number of lead fields to be used in your form emails. These can be easily placed within your emails and will be automatically replaced with the appropriate text once the email is sent.

### Opened Email Tracking ###

Each email sent through Mautic is tagged with a tracking pixel image. This allows Mautic to track when a lead opens the email and execute actions accordingly. Note that this technology is limited to the lead's email client supporting HTML and auto-loading of images. If the email client does not load the image, there is no way for Mautic to know if the email was opened.

### Unsubscribing and Double Opt-In ###

Mautic has a built in means of allowing a lead to unsubscribe from email communication. If using the builder, simply drag and drop the Unsubscribe Text or Unsubscribe URL tokens into your email. Or insert {unsubscribe_text} or {unsubscribe_url} into your custom HTML. The unsubscribe text token will insert a sentence with a link instructing the lead to click to unsubscribe. The unsubscribe URL token will simply insert the URL into your custom written instructions. 

Mautic currently does not have a built in way of handing double opt-ins (although it is planned). It can be achieved through the use of lead lists, a custom lead field, a landing page and a campaign. To configure such a scenario, consider the following:

1. Create a lead list without filters for leads pending double opt in. 
2. Create a boolean custom lead field for the double opt-in notation and set the default value to 0.
3. Create a landing page that will serve as the "confirmation page" for the double opt-in.
4. Create a confirmation email and insert the token for the confirmation landing page (if using the builder, drag and drop the specific page into the email or if using custom HTML, insert {pagelink=ID} where ID is the id of your landing page). The token will be replaced with the URL of the landing page.
5. Create a campaign to automate the double opt-in dripflow and assign it the lead list from step 1. In the Campaign Builder, start by adding a "Send email" action and select the confirmation email to be sent. Connect that into a "Visits a page" decision. You may be tempted to use the "Opens email" decision, but for this scenario, it's not the opening of an email that matters rather the lead taking the extra step to click the link to confirm. So use the "Visits a page" instead and select your confirmation landing page in the the "Limit to Pages" dropdown. Add a "Update lead" action, enter a 1 for the double opt in field, save then connect it to the green decision point of the "Visits a page" decision. Finally, add and connect a "Modify lead's lists" action to the same decision point to remove the lead from the pending confirmation lead list.
6. Whenever you create the other lead lists, use the double opt-in field as a filter by setting it to equal 1 to exclude leads who have not gone through the double opt in process.

An example flow may be something like this. A lead subscribes to your newsletter through a Mautic form. The form's submit actions creates the lead and adds them to the "Pending Confirmation" list. The lead is automatically added to the "Double Opt-In" campaign which will send the confirmation email. When the lead clicks on the link to visit the "Thank You for Subscribing" landing page, the double opt in field will be updated and the lead removed from the "Pending Confirmation" lead list. You can now filter leads based on who has opted in and who has not.