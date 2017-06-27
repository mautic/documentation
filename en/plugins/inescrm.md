# Plugin Mautic - INESCRM

This plugin allows you to push you contacts from Mautic to INESCRM  with the "push contact to integration" action.
If you do not see the plugin in your plugin list, be sure you are in a version published after 2.9.0.

If you don't have an INESCRM account yet, [create one here](http://www.inescrm.fr/).

## Plugin configuration

1. In the *configuration* menu > *custom fields*, add 2 new fields *Text* or *Number*, that will hold INESCRM contact IDs.
They can be named as you like (eg: `ID contact INES` & `ID client INES`) and belong to any field group.

2. In the *configuration* menu > *plugins*, if you don't see the INESCRM plugin, click on *Install / Upgrade Plugins*. Then clicj on the INESCRM plugin and configure with you CRM access code: *Account*, *User*, *Password*. And test the connexion.

3. When the connexion is OK, save configuration, close and open again.
The *Contact Field Mapping* tab must be displayed.
In this tab, map `Référence contact chez INES` & `Référence société chez INES` to the Mautic fields created on step 1.
Then map the extra fiels you when to synchronize.
Notice that some fields are existing twice for the contact and company fields.
**In the next version, the Company Field Mapping tab will be introduce to avoid that.**

4. Enable features wished in *Features* tab.

5. In the *Enable/Auth* tab, turn *Published* button to `ON`.

## Features

* *Push contact to integration* enable the action holding the same name in forms, campaigns and points triggers.
* *Full synchronization* allows to send all the contacts from Mautic to INESCRM having at least an email address and a Company. To work you need to install the following CRONJOB:
`php app/console crm:ines [--number-of-leads-to-process=]`
The parameter `number-of-leads-to-process` shows the maximal amount of leads to synchronize on each call.
* The *Open sync. log* button displays the queue, limited to 200 rows, of last synchronisation planned, succeed or failed. this queue is used only by the "full-sync" mode.
In case sync. error, a new try will be queued. After 3 fails, the row will be displayed as 'FAILED' and ignored for the next sync.
* The contact fields checked in the **features** tab become non-erasable: the Mautic values do not erase the INESCRM values if existing.

## Initial synchronisation

When the *Sync. all leads* mode is enabled, the CRONJOB checks each time the queue is empty, if there is any lead in the Mautic database that has never been synced and add them to the queue.
Then, you don't have to care about the initial synchronization that will be handled automatically.

## Test the plugin

Follow [these steps](./../plugins/integration_test.html).

## Credit

this plugin has been developed by [@webmecanik](https://github.com/webmecanik) in collaboration with [@jcdeveloppement](https://github.com/jcdeveloppement).
