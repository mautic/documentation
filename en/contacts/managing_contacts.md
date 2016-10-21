# Manage Contacts

The manage contacts page is the main interface through which you can view and interact with your contacts - both visitors and standard contacts.

## Segments

The segment is the default tabular view of all the contacts in the system - by default the **list view** is enabled, but you can also choose to switch to the **card view** (also known as **grid view**) which uses avatars to depict the contacts visually using cards. Clicking the appropriate button on the top right will allow you to switch between the two views.

Hint: If you prefer using keyboard shortcuts you can enter "t" on your keyboard to dynamically switch to table view and "c" to switch to the card view.

## Searching for contacts

The segment can be searched using the box at the top of the list, and can be ordered using the table headings by clicking on the heading you wish to sort the list by.

![](/contacts/media/contacts-search.jpg)

The search box allows many different search types and follows the same search process and variables as found in all other search layouts. You can learn more about the powerful search options available on the search documentation page.

## Adding contacts quickly

If you have contacts you would like to quickly add to Mautic manually, and they are not in the system as part of the normal workflow (for example by completing an inquiry form or having been imported) you can use the Quick Add Contact button to add them to the system.

You can of course also add them through the New Contact form and add much more detail but for quick entry this is the easiest and fastest way to get the contact into the system.

## Adding contacts normally

If you have contacts to import and you have time to add all the information, click on the dropdown arrow to the right of 'Quick Add Contact' and select 'New'.  This opens the new contact screen, where you can enter all the information you have about the contact.  Use the tabs at the top to add custom fields and social network profiles.

## Importing contacts

Mautic offers the ability to import contacts from other sources via CSV file - this is a great way to get up and running quickly if you need to import a lot of contacts at once.

To use the import facility, make sure that you first have all the fields set up under 'Manage fields' which correspond to the information you are importing - you don't want to lose any data if at all possible.

Once you have created all the contact fields, click on the dropdown arrow to the right of the Quick Add Contact button, and select 'Import'.

Upload your CSV file, and ensure that you match the delimiter, enclosure and escape characters so that the importer can understand the data.

When you click on 'Upload' you will have the opportunity to match the fields found in the CSV file to the fields that you have in Mautic, which will allow the data to be correctly imported.

Following values will result in TRUE when importing a Boolean value: `1`, `true`, `on` and `yes`. Those values can be also capitalized and still taken as TRUE. Any other value will be saved as FALSE.

## Editing contacts
To edit a contact, click on the name of the contact (or the IP address if the visitor is anonymous) to open the contact screen.

From this screen, you can view the recent events and any notes that have been made against the contact.

To edit the contact, click on the 'edit' button on the top-right menu.

## Contact duplicates

When Mautic tracks contact's actions like page hits or form submissions, it will automatically merge the contacts by unique identifiers which are:
- IP address
- Email _(or any other contact field you mark as unique identifier)_
- Cookie

If Mautic knows only the IP address, it will merge the contact action (page hit, form submission etc.) with a contact with the same IP address. If the IP address does not exist in the Mautic database yet, it will create a new contact. But if Mautic knows the unique cookie, it will merge the actions to the contact with the same cookie or creates a new one.

If a contact sends a form with an email address, it will merge the submission with the contact having the same email address. Even if the IP address or the cookie matches another contact.

So Mautic will take care of duplicate contacts created by the event tracking. But you can still create a duplicate contact via the Mautic administration. As of Mautic 2.1.0, you will be notified if there is already a contact with the same unique identifier.
