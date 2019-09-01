# Contacts

Leads were renamed to contacts in Mautic 1.4.0.

Contacts are the central factor of a marketing automation platform. These are all the individuals who have visited your websites or interacted with you in some way.

### Contact Types

There are two types of contacts:
* **Visitors** (formerly anonymous leads) — visitors to your site who have not yet been identified by a form or other interaction.
  * These contacts are tracked by Mautic but typically remain hidden so as not to clutter your segment.
* **Standard contacts** — contacts which have identified themselves via a form or some other source. As a result, these contacts typically have a name, email, and other identifying fields.

#### Visitors (formerly anonymous leads)

Anonymous leads were renamed to visitors in Mautic 1.4.0.

You can view visitors by using the 'table view' (use the "t" keyboard shortcut to view contacts in a table or "c" as cards) within the contacts section.

Visitors are worth tracking, because these could be future customers. By tracking them before they have any interaction, you can retain a log of when they visited your site, which allows you to get a picture of their activity prior to engaging with you.

##### Search Text
You can use the filter in the Contacts screen to display only visitors by using the following command in the search bar above the contacts list:

```
is:anonymous
```
##### Screenshot

![](media/contacts-anonymous.jpg)

The resulting list will display those IP addresses which have not yet provided identifying information.

#### Standard Contacts

The second type of contact is a standard - or known - contact. These contacts have identified themselves via a form or other source. You may also have more information about them from previous interactions, or from a third-party system such as a Customer Relationship Management (CRM) tool. As a result, these contacts typically have a name, email, and other identifying information which can be associated with the contact.

The standard contact is the preferred contact within Mautic. These are contacts which may have started as a visitor, but at some point provided additional information such as a name, email address, social network handle, or other identifying characteristics which have enabled you to connect up the activity on your website with a known person. You can nurture these contacts through the Mautic marketing automation platform, learn more about their behaviour, and take specific actions as a result of this information.

The [Manage Contacts](https://www.mautic.org/docs/en/contacts/managing_contacts.html) section provides more information on how you can work with contacts in Mautic.