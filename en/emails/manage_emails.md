# Manage Emails

### Email Overview

The email overview allows at-a-glance information regarding the success or failure of a particular email. You can quickly see relevant information in regards to opens, bounces, successful click-throughs and other important statistics.

### Email Creation

Email creation can be handled through the graphical email builder with little to no HTML knowledge. Emails are assigned to particular segments and/or campaigns. Below are some key steps to be performed when creating an email.

### Segments

When creating an email you can select the segments to which you want to send the email.

![](http://drop.dbh.li/image/0p3P3c2O3P1e/Image%202014-11-18%20at%2011.25.34%20PM.png)

This entry field is a multi-select which allows you to choose several segments if necessary.

### Email Builder

The email builder is a graphical user interface to create an HTML email through the use of drag-and-drop tools.

The email builder provides quick and convenient access to assets, landing pages, and other extra fields which are considered important or commonly used.

### Base64 encoded images

Since Mautic 1.4, there is a new option in the Mautic configuration, the Email Settings tab. You can let Mautic encode all images in the email text as base64. It will attach the image inside the email body. It has several implications:

- The main idea with this option is that most of the email clients will display the images directly without any approvals.
- However, some email clients like Gmail will require the approval because of the tracking pixel and won't display the base64 encoded images anyway. See the next paragraph for possible solution.
- The email body will increase significantly if the email contains many and/or big images. Some email clients like Gmail will "clip" such email and won't display it directly.

### Disable the tracking pixel

As described above, some email clients display the image approval if one of the images is loaded from remote location. Like the tracking pixel. If you care more about this approval than the email open tracking, you can disable the tracking pixel. Then the images should be displayed directly without any approval.
