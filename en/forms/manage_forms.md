# Manage Forms

The new form view lets you create a form and attach any fields you want to collect from your users. After you've created the fields you can then define what actions you want to perform after the user submits the information.

### Form Overview

The form overview provides a quick overview of the submissions received over a time period to easily analyze how successful a particular form is. The bottom of the form overview outlines the fields and actions included as part of a particular form.

### Form Fields

A form can contain as many fields as needed. These fields can be laid out dynamically by the system or handled via HTML if you want more control.

![](/forms/media/new-form.jpg)

### Form Actions

Form actions are items to be handled on the submission of the form. You can define multiple actions to be performed on each submission.

![](/forms/media/form-actions.jpg)

#### Creating and Updating Contacts with Forms ####

To have your form create or update contacts (in order to update, there must be a matching email), add the Create/Update Contact submit action. Map the fields from the form to your contact fields. **Note, it is important that this action be ordered first so that the contact's details are available for subsequent actions.** Think of it as the contact has to be created or updated before it can be added to segments, pushed to integrations, etc.

### Kiosk mode

The kiosk mode is helpful when you know that some form will be submitted from one device by multiple contacts. For example like a kiosk at a conference. When the kiosk mode is turned on, each submission will create new contact. When a kiosk mode is turned off, Mautic will edit the contact which belongs to the current session.

### Form Injection

There are three ways you can use the form. You can copy the entire output or you can have the form injected dynamically using the provided javascript. These are two options for directly including the form on a page, you can alternatively embed the form directly in a Mautic landing page if you choose.

![](http://drop.dbh.li/image/2M1q3T2T0Z0u/Image%202014-11-17%20at%204.20.56%20PM.png)

**It is recommended to do not paste the injection code twice, it risks to create troubles on the submit form action when mandatory fields are submitted empty.**

### Form results

When on the form overview page you can click the Results button located in the top right to open a tabular view of all form submissions. These results can be easily filtered and sorted by each column heading.

### Form Preview

The form preview provides a popup overview of what the form will look like. Remember that form styling is controlled by the surrounding page or website content and thus will display differently in final layout then in the preview.

### Pre-populate a form field value

It is possible to pre-populate the value of a form field from the URL query parameters.

The contact field's alias can be obtained from the table when viewing Contacts -> Manage Fields. The form field's name is stored as the alias in the database and is auto generated from the field's label; you may have to look at the source of your form to get the exact name (open the form and click the preview button). For example, here is a sample html section taken from a form. The name to use is what's within `mauticform[FIELDNAME]`.

```
<div class="mauticform-row mauticform-email mauticform-row-email" id="mauticform_email">
    <label id="mauticform_label_email" for="mauticform_input_email" class="mauticform-label" "="">Email</label>
    <input id="mauticform_input_email" name="mauticform[email]" value="" class="mauticform-input" type="email">
</div>
```

#### Pre-populate the values automatically in an email

Embed the tokens {leadfield=FIELDALIAS|true}, one for each contact specific information you want to pre-populate the form with, into the URL, assigning them to the name of your form field.The |true tells Mautic to URL encode the value so that it works in the browser.
```
{pagelink=1}&email={leadfield=email|true}
```
In the rendered email sent to a contact, the URL may be converted into something like:
```
http://my-mautic.com/my-landing-page?ct=A_REALLY_LONG_STRING&email=contactemail%40gmail.com
```
So, what happened is `{pagelink=1}` was converted into the landing page URL and had `?ct=A_REALLY_LONG_STRING` appended. The really long string is encoded information about the contact which includes the contact ID. Each `{leadfield=FIELDALIAS}` was replaced with the contact's data. When the contact clicks the link, they will be taken to the landing page with the embedded form, and the form's 'email' input will be pre-populated with the value passed through the URL.
