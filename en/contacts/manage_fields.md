# Manage Custom Fields

You can manage Custom Fields through the _Admin_ menu (click the cogwheel upper right hand side of Mautic).

![access admin menu](media/access-admin-menu.png)

![admin menu](media/admin-menu.png)

## Custom Fields

The _Custom Fields_ page will let you view all existing Contact fields as well as any custom contact fields you have created.

![custom fields](media/custom-fields.jpg)

You will notice the group column which will show you where the specific field will be shown on the _Contact profile_. In the last column, you may see several icons which signify various properties of the field:

![custom field icons](media/custom-field-icons.jpg)

1. Lock icon - These fields are unable to be removed as they are used by the core installation.
2. List icon - These fields can be used as filters of segments.
3. Asterisks icon - These fields are required when filling in the contact form
4. Globe icon - These fields are publicly updatable through the [tracking pixel][variables] URL query (see [Contact Monitoring][contact monitoring] for more details).

### Published Fields

There is a toggle switch which shows before each label title.\
This type of switch is used throughout the Mautic UI to publish and unpublish items.

![unpublish fields](media/unpublish-fields.gif)

### Adding A New Field

You can create additional custom fields and define the data type you want that field to hold. In addition to the data type you will also select the group for that particular field. This will define where the field displays on the Contact edit and detail view.

![new custom field](media/new-custom-field.jpg)

[contact monitoring]: <contact_monitoring.html>
[variables]: <./../setup/VARIABLES.html>
