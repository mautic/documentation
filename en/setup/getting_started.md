# Getting Started

Awesome! You've downloaded a marketing automation tool. That's a great first step, but now you wonder where to go from here. Follow this very simple guide to get started using your shiny new toy!

## Step 1: Install Mautic

If you have already downloaded the zip from the download page or have installed Mautic through some other source (Softaculous, Bitnami, Digital Ocean etc...) then you have already completed the first step. If not then you will need to upload the Mautic package (a zip file) to your server; unzip the files; and then navigate to that location in your browser. You will find Mautic has a very easy to follow on-screen installation process.

## Step 2: Add Cron Jobs

Once you've installed Mautic you will need to create a few standard cron jobs to have your software process various tasks. These cron jobs can be created through a cPanel or added through command line. If you are unfamiliar or uncomfortable with this step then we'd recommend asking in the forums or in the live Slack chat. Here is a list of the cron jobs you'll need to create.

**Updating Segments**

`php /path/to/mautic/app/console mautic:segments:update`

**Update Campaigns**

`php /path/to/mautic/app/console mautic:campaigns:rebuild`

**Execute Campaign Actions**

`php /path/to/mautic/app/console mautic:campaigns:trigger`

Review [Cron Jobs](./../setup/cron_jobs.html) for more information on these and other optional cron jobs.

## Step 3: Download the IP lookup service database

By default, Mautic installs set to use MaxMind's free GeoLite2 IP lookup database. Due to the licensing of the database, it cannot be included with Mautic's installation package and thus must be downloaded. Click on the cogwheel in the upper right hand of Mautic to view the Admin menu then click Configuration. On the System Settings tab, scroll down to find the IP lookup service option and click the "Fetch IP Lookup Data Store."

You could also choose another supported IP lookup service if you prefer.

## Step 4: Install the Tracking Javascript

After installation and setup of the cron jobs you're ready to begin tracking contacts. You will need to add a simple javascript to the websites for each site you wish to track via Mautic. This is a very simple process and you can add this tracking script to your website template file, or install a Mautic integration for the more common CMS platforms. Here is an example of the tracking javascript:

``` <script> (function(w,d,t,u,n,a,m){w['MauticTrackingObject']=n; w[n]=w[n]||function(){(w[n].q=w[n].q||[]).push(arguments)},a=d.createElement(t), m=d.getElementsByTagName(t)[0];a.async=1;a.src=u;m.parentNode.insertBefore(a,m) })(window,document,'script','http(s)://yourmautic.com/mtc.js','mt'); mt('send', 'pageview'); </script> ``` 

You'll need to change the site URL (replace yourmautic.com with your own URL) in the above script.

Checkout [Contact Monitoring](./../contacts/contact_monitoring.html) for more details.
