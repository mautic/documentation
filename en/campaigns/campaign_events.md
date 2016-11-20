## Campaign Events

Below are notes on some of the specific campaigns events. 

### Campaign Actions

#### Send Email - Marketing vs Transactional

![](/campaigns/media/send-email-delay.png)

In the send email action, there is an option to select Transaction or Marketing. A transactional email is one that can be sent to the contact multiple times. A marketing email is one that only be sent to the contact once across multiple sources (e.g. another campaign). If the contact has already received this email from another source or the current campaign, the email will not be sent again and the contact simply progresses on through the campaign. 

### Campaign Decisions

#### Opens Email

The opens email decision can only be attached to a send email action. Whatever email is sent through the action is the email used by the decision. 

#### Visits a page

Decision works with landing page (Limit to Pages field) .

Also works with every page where you're useing Mautic tracking code (URL or Referrer field). You are able to use search expression with **Like** operator for your matches. Both fields use [fmatch](http://php.net/manual/en/function.fnmatch.php).

Note: This decision use OR operator between fields (Limit to Pages field, URL, Referrer).

![](/campaigns/media/vists-a-page.PNG)