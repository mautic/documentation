# Manage themes

## Theme Manager

Since Mautic 2.1.0, the Theme Manager was added and you can access it via the Admin Menu (click the cog icon in the top right corner to open it), select the Theme menu item.

The table of installed themes shows you the name of the theme, the author name and the link to his website if provided and what features the theme provide. There is also preview (if provided) to see the screenshot of the theme under the arrow next to the theme name.

### Install new theme

A new theme can be installed as a zip package. The zip package must have the same structure has the themes preinstalled at Mautic. Than means there must be the config.json file present in the root folder of the zip package. More on that can be found in the [developer documentation](https://developer.mautic.org/#theme-directory-structure).

If you have the theme zip package either created by yourself or downloaded from a theme provider, in the top right corner of the Themes page is the upload form. Click the "Choose File" button to choose the zip file, then click Install. The notice will appear if the installation was successful and if so, the new theme appears in the table of currently installed themes.

### Update an old theme

The old theme files will be rewritten by the new one when installing a theme which already exists in your Mautic. Therefore, the theme updates can be also done by the Theme Manager's Install form.

### Delete a theme

Go to the Theme Manager, check what theme(s) you want to delete and then click the red button above the theme table to delete them.

## Assigning a default theme

It is possible to assign a default theme to a Mautic instance by editing the global configuration.  To access the global configuration you must be logged in with sufficient access.  Click on the cog icon beside the logged in user, and select 'Configuration'.

From the configuration screen, the available themes will be listed in a dropdown box, which can be selected.  On saving, this setting will apply for all resources which do not have a theme explicitly specified.

![Configure themes under Administration Settings->System Settings](/themes/media/theme-config.jpg)

To assign a theme to a specific resource - such as a landing page - select the theme from the dropdown, and save the resource.

![Select a theme for a new page](/themes/media/theme-page-builder.jpg)

