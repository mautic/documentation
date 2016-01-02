# Mautic Documentation

### Introduction
This book serves as the [documentation for Mautic](https://www.mautic.org/docs/index.html), the open source marketing automation system. Just as the code is open source and available for everyone, so is the documentation. Everyone is welcome to help make this information better and improve as needed.

### Getting Started

Awesome! You've downloaded a marketing automation tool. That's a great first step, but now you wonder where to go from here. Follow this very simple guide to get started using your shiny new toy!

#### Step 1: Install Mautic

If you have already downloaded the zip from the download page or have installed Mautic through some other source (Softaculous, Bitnami, Digital Ocean etc...) then you have already completed the first step. If not then you will need to upload the Mautic package (a zip file) to your server; unzip the files; and then navigate to that location in your browser. You will find Mautic has a very easy to follow on-screen installation process.

#### Step 2: Add Cron Jobs

Once you've installed Mautic you will need to create a few standard cron jobs to have your software process various tasks. These cron jobs can be created through a cPanel or added through command line. If you are unfamiliar or uncomfortable with this step then we'd recommend asking in the forums or in the live Slack chat. Here is a list of the cron jobs you'll need to create.

**Updating Lead Lists**

`php /path/to/mautic/app/console mautic:leadlists:update`

**Update Campaigns**

`php /path/to/mautic/app/console mautic:campaigns:update`

**Execute Campaign Actions**

`php /path/to/mautic/app/console mautic:campaigns:trigger`

Review [Cron Jobs](./setup) for more information on these and other optional cron jobs.

#### Step 3: Download the IP lookup service database

By default, Mautic installs set to use MaxMind's free GeoLite2 IP lookup database. Due to the licensing of the database, it cannot be included with Mautic's installation package and thus must be downloaded. Click on the cogwheel in the upper right hand of Mautic to view the Admin menu then click Configuration. On the System Settings tab, find the IP lookup service option and click the "Fetch IP Lookup Data Store."

You could also choose another supported IP lookup service if you prefer.

#### Step 4: Install the Tracking Pixel

After installation and setup of the cron jobs you're ready to begin tracking leads. You will need to add a single tracking pixel to the websites for each site you wish to track via Mautic. This is a very simple process and you can add this tracking pixel to your website template file, or install a Mautic integration for the more common CMS platforms. Here is an example of the tracking pixel:

`<img src="http://yourdomain.com/path/to/mautic/mtracking.gif" />`

Checkout [Lead Monitoring](./leads/lead_monitoring.html) for more details on the tracking pixel.