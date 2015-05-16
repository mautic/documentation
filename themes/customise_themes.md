# Customising themes

It is possible to customise themes, or even to create your own from scratch, with Mautic.  To do this you need to have access to a file transfer system such as FTP or SSH.

## Customising an existing theme

To customise an existing theme, it is recommended to make a copy of the entire theme folder, and rename it.  Following renaming the folder, edit the following files to amend the theme paths and name:

* theme.css - rename to match your theme name
* config.php - amend theme name
* base.html.php - amend file path for CSS import to use new folder and CSS filename; amend the default page title from 'Mautic'

Mautic themes are written in HTML and PHP, to make amends to the structure or layout simply edit the files in the new theme and upload them to your instance.  Ensure that your hosting provider does not have caching enabled, as this can sometimes prevent changes to CSS files being replicated instantly.

## Adding new positions

To add new positions, firstly edit config.php and append a line which includes the new position name.  Secondly, either include the new position in one of the existing arrays in the relevant file within the HTML folder, or create a new array.  This can be simplified by copying an existing code block and pasting it, modifying the names of the divs and the positions being loaded.
