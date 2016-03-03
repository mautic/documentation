# Theme structure

## Folder structure

Themes are located inside individual folders - one per theme - within the directory structure of a Mautic installation.  This folder should be accessed using a file transfer system such as FTP or SSH.

![Theme folder structure](/themes/media/themes-folderstructure.png "Theme Folder Structure")

## File structure

Mautic themes generally follow a similar structure, as can be seen in the themes which ship with a basic installation.

![Theme file structure](/themes/media/themes-filestructure.png "Theme File Structure")

Within the theme folder there are subfolders which contain the CSS files, PHP files, and in some cases, image files.  There is also a config.php file which contains the base settings for the theme.

### Config.php

The configuration file includes an array which specifies the name of the theme, features available (e.g. landing page template, email template, form template etc) and the positions which are available in the landing page and email templates to be used.

### CSS
Within the CSS folder are contained any stylesheets which are required by the theme, usually named according to the theme name - for example, mauve.css.

Styling used in themes can be adjusted and altered, however it is sensible to clone the theme and rename it, making edits in the clone, rather than edit the core files directly.

### HTML
The HTML folder contains the files which control the layout of the different aspects of Mautic.

Generally a theme will include the following files:

* base.html.php
* email.html.php
* form.html.php
* message.html.php
* page.html.php

#### base.html.php
This file contains the basic structural layout for landing pages, including the <head></head> tags, and importing any stylesheets and javascript that may be required.

#### email.html.php
This file contains the structural layout and inline styling which controls the look and feel of emails.

#### form.html.php
This file controls the layout, look and feel of forms which are associated with the theme, including semantic markup.

#### message.html.php
This file is used to display messages - such as the post-submission messages on a form.

#### page.html.php
This file controls the layout, position and semantic markup for landing pages.

### Images
If images are used within a theme, they can be stored in the images folder.  This folder may not be present if images are not being used by a theme.

