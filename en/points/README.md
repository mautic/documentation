# Points

Points provide a way for contacts to be properly weighted. These points have both triggers and actions. Each term will be properly defined and a thorough understanding of how points function will ensure that your overall marketing automation process is successful.

### Point Actions

Point actions are those times when a contact receives a change in their point total. These actions can be either positive or negative point changes and are based on a particular action as you determine.

A partial list can be seen in the screenshot below.

![](/points/media/new-point-action.jpg)

Please note that an action can only be triggered once upon each contact.
For example, you can't create for now a general rule to add 10 points each time a contact download any asset, the action and points modifications will be launched when the contact download his First Asset concerned by the Actions Rule.

You can choose which published Score Category (see below) will be affected by your action using the Score Category's dropdown. Leave Global Score to modify the Contact's default Score.

![](/points/media/points-actions-scorecategories.jpg)

Clearly these actions can be expanded upon as needed. 
This is the essence of point actions. 

The other part of the points system are the triggers. They are defined next.

### Point Triggers

Point triggers are resulting events which are fired based on the achieved point total of a contact.

In simple terms, when a contact reaches a minimum number of points, the point trigger is fired and an action is performed.
Please note the trigger can concerns the Contact's Global Score or any published Score Category (see below).

When creating a point trigger you have the option to apply the trigger to all existing and applicable contacts as well as new contacts.

![](/points/media/new-point-trigger-action.jpg)

These point triggers and associated events are also fully customizable.

### Score Categories

Score Categories have been introduced into Mautic to let Mautic's users track points modifications against multiples "categories".
Depending on your business, if your services portfolio concerns multiples and differents solutions, it could be interesting to track visitors' interest per Business Unit or per Service.

A visitor can in deed visits the "Solution A" part of your website and don't want to be embedded in a default marketing campaign that will present and promote "Solution B".

Creating Score Categories will allow you to design new specific scores for each Contacts and Companies.

You can access the currently defined Score Categories clicking the Manage Score Categories link into the Points Menu.

![](/points/media/list-scorecategory.jpg)

Please note that a default entry "Global Score" will always be present "out-of-the-box" and represents the global score point you can retrieve on both Contacts and Companies page. 

This global score can't be edited or deleted from the system as it is the base score category always implemented into Mautic.

Creating a new Category only needs a few extra information

![](/points/media/new-scorecategory.jpg)

Enter the Score Category name, select the Display Order (see below) and choose if a score modification to this category affects the global score (Yes/No) and in which ratio (Enter the Percentage).

If set to Off, any update to the Score Category will not be reflected to the Global Score.
If set to Yes, the quantity of points added/removed from the Score Category will also be added/removed to the Global Score and the radio will be multiplied before application.

For example : when you add 100 points to Score Category "Business Unit 1", you can add 100 points to the Global Score by enabling the switch and set the ratio to "100%".

#### Score Categories Order

Order in Score Categories are only used for convenience purposes on the Contacts/Companies screen to display the Score Categories in the specified order and then by alphabetical names, this allow Mautic users to choose to display a Score Category labelled "Service" before a less important Score Category labelled "Product" for example.

So Score Categories display order is defined by the combination of the category's order and then by the Score Category's name (in case two Score Categories contains the same order value)

![](/points/media/contacts-scorecategories-order.jpg)

#### Deletion of a Score Category used in Mautic

When used in Point Action, Point Trigger, on a Form's action or a Campaign, the Score Category defined can't be deleted from the database, that's why the checkbox option will be greyed out.
Anyway if you try to select the delete dropdown, a popup message will warn you how and where the score category is used and will prompt you first to edit the necessary actions before being allowed to delete the score category.

![](/points/media/delete-scorecategory.jpg)
