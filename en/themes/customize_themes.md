# Customizing themes

It is possible to customize themes, or even to create your own from scratch, with Mautic. To do this go to the Theme Manager, open the drop down menu next to the pre-installed theme you want to modify and download it.

## Customizing an existing theme

To customize the downloaded theme, unzip the files to an empty folder. Name the folder as the new name of your theme. Then edit the following files to amend the theme paths and name:

* theme.css - rename to match your theme name
* config.php - amend theme name
* base.html.php - amend file path for CSS import to use new folder and CSS filename; amend the default page title from 'Mautic'

Mautic themes are written in HTML and TWIG, to make amendments to the structure or layout simply edit the files in the new theme and upload them to your instance.  Ensure that your hosting provider does not have caching enabled, as this can sometimes prevent changes to CSS files being replicated instantly.
