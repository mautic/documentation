# Citrix Plugins

## Description

The plugins pull data from Mautic and push data to Mautic from these products:

- _GotoMeeting_
- _GotoWebinar_
- _GotoTraining_
- _GoToAssist_

## Features

1. Create registrants in _GoToWebinar_ and _GoToTraining_ based on Campaign decisions, Contact data and also from registration Forms in Mautic
1. Use registrant and attendee information in Segments (filters), Forms and Campaigns (actions and decisions).
1. Display _GoToWebinar_ and _GoToTraining_ attendance as an additional activity on the Contact timeline
1. Send emails with buttons to start _GoToMeeting_, _GoToTraining_ and _GoToAssist_ sessions

## Plugin activation instructions

> **Note**
>
> These examples use _GoToMeeting_ and _GoToWebinar_, but it's the same for _GoToTraining_ and _GoToAssist_

1. Enable the plugins you need

![Citrix plugins](https://cloud.githubusercontent.com/assets/2924026/19797584/54467954-9ca9-11e6-8e31-f80f7469fe84.png)

1. Activate the plugins with the [Citrix Developer][citrix-developer] API keys

![image](https://cloud.githubusercontent.com/assets/2924026/19797588/5c6ce640-9ca9-11e6-981c-a98a728e1712.png)

- Use the Consumer Keys from the [Citrix developer][citrix-developer] website

![image](https://cloud.githubusercontent.com/assets/2924026/19797595/612744f0-9ca9-11e6-90b0-566fdff69ef4.png)

## New integrations

### Segments

#### New filters

New Segment filters will be available

![new segment filters](https://cloud.githubusercontent.com/assets/2924026/19797599/655fb6ce-9ca9-11e6-9d27-9ec295068a1a.png)

- Past _GoToProduct_ sessions will be available to choose from

![past sessions available](https://cloud.githubusercontent.com/assets/2924026/19797600/69dd3604-9ca9-11e6-8212-7a0a383bff34.png)

### Forms

#### New fields

New Form fields will be available

![new form fields](https://cloud.githubusercontent.com/assets/2924026/19798154/9954bf30-9cac-11e6-8173-06acc0ca1fa1.png)

- The fields will display the available events for each product

- The Form will validate that the mandatory fields are present

![form fields](https://cloud.githubusercontent.com/assets/2924026/19797605/72ec51e4-9ca9-11e6-8416-be31a013c8d1.png)

#### New actions

New Form actions will also be available

![new form actions](https://cloud.githubusercontent.com/assets/2924026/19797611/7699f9c2-9ca9-11e6-96f5-d90dcafcbd3f.png)

- Each action will permit to select a single event or let the user select from the form.

- They also include fields to map to obligatory lead fields

![form field mapping](https://cloud.githubusercontent.com/assets/2924026/19797613/7b25eb68-9ca9-11e6-99c7-d9f4053136ac.png)

#### Form examples

##### User selects an event from a list

- Select event

![select event from list](https://cloud.githubusercontent.com/assets/2924026/19797614/7eea2f02-9ca9-11e6-86dd-c895bb0d65c3.png)

- Form submitted

![form submitted](https://cloud.githubusercontent.com/assets/2924026/19797632/9122e614-9ca9-11e6-991c-70b2033ea6c9.png)

##### Send Start button link

The Send Link actions require an email object with a Token to insert the link of the event.  The available tokens are shown.

![send link action](https://cloud.githubusercontent.com/assets/2924026/19797615/82b326f2-9ca9-11e6-9d30-1324b7efd49a.png)

### Campaigns

#### New Campaign conditions

New Campaign actions will be available

- New conditions for registered and attended contacts

![campaign condition](https://cloud.githubusercontent.com/assets/2924026/19797618/8693fb8e-9ca9-11e6-8ae2-44b67f05769e.png)

#### New Campaign actions

New Campaign actions will be available

- Select the event and the email template to send (if applicable)

![campaign action](https://cloud.githubusercontent.com/assets/2924026/19797619/8a501b68-9ca9-11e6-8232-d5c23b9cf445.png)

#### Campaign examples

##### Send a webinar start link to registered Contact

This is an example of a Campaign that:

- includes Contacts from a source Segment
- identifies Contact as having registered for a webinar
- sends a start link to event _Preliminary Meeting_

![campaign send start link](https://cloud.githubusercontent.com/assets/2924026/19797623/8d7b1252-9ca9-11e6-9370-b3f05cc08ee1.png)

- The email with the link (that was injected with the Token) is viewed in the browser

![email with start meeting link](https://cloud.githubusercontent.com/assets/2924026/19797642/986c9c30-9ca9-11e6-9233-5e826f2520b9.png)

- When the contact clicks on the link, it redirects to _GoToMeeting_ to start the meeting

![start meeting](https://cloud.githubusercontent.com/assets/2924026/19797644/9c6e43ce-9ca9-11e6-8f45-ec36b19502fa.png)

### Contacts

#### Contact timeline

New events appear in the Contact's timeline

![contact timeline](https://cloud.githubusercontent.com/assets/2924026/19797638/9484bb7a-9ca9-11e6-9a18-62eab010378e.png)

#### Contact examples

##### Attended webinar

This is an example of a webinar where the contact attended.

![attend webinar](https://cloud.githubusercontent.com/assets/2924026/19797647/a012bfb4-9ca9-11e6-8d27-92edfb071bfb.png)

When the [cron job][cron] that synchronizes the data runs, it retrieves the new state of the contact and the data is visible on the timeline as an attended event

![contact timeline](https://cloud.githubusercontent.com/assets/2924026/19797652/a435ee36-9ca9-11e6-9936-17cd19384452.png)

### Synchronize events data cron job

The [cron job][cron] to synchronize the events is

    php app/console mautic:citrix:sync

    Usage:
        mautic:citrix:sync [options]

    Options:
        -p, --product[=PRODUCT]  Product to sync (webinar, meeting, training, assist)
        -i, --id[=ID]            The id of an individual registration to sync

### Update: Join _GoToWebinar_ button token

Follow these steps to include a _GoToWebinar Join Button_ in a Segment email:

1. Create a webinar in the [GotoWebinar website][GotoWebinar]

1. Create a new contact and use the email address to register for the new webinar

1. Run the Citrix Sync console command: `php app/console mautic:citrix:sync` so that the webinar information is retrieved to the database.

1. Create a Segment with a "Webinar (registered)" filter.

    > **Note**
    >
    > This is mandatory, and it will be validated when trying to save the email with the token in the body

    ![edit Segment](https://cloud.githubusercontent.com/assets/2924026/24730532/5ff1f31e-1a21-11e7-9e5f-fbdc604c0883.png)

1. Add the Contact to the Segment manually or by running `php app/console mautic:segments:update`

1. Create a new Segment Email and assign the previously created segment.

    ![new Segment Email](https://cloud.githubusercontent.com/assets/2924026/24730574/95b6083c-1a21-11e7-8c79-a8b9c45ab810.png)

1. Open the email Builder and insert the _GotoWebinar Join Button_ token:

    ![email builder](https://cloud.githubusercontent.com/assets/2924026/24730644/0f294076-1a22-11e7-9af8-edd359587a41.png)

    The button can be styled by overriding the `citrix-start-button` CSS class.

    ```css
    .citrix-start-button {
    background: green !important;
    }
    ```

1. Send the email to the Segment contacts.

    ![send email](https://cloud.githubusercontent.com/assets/2924026/24730930/ddef679a-1a23-11e7-9610-513a44bcfd48.png)

1. The email arriving in the new Contact's Inbox should include a button to join the webinar with the appropiate URL for the contact.

    ![join webinar email](https://cloud.githubusercontent.com/assets/2924026/24731148/72272370-1a25-11e7-97ac-e04943f25775.png)

### Update: How to Create a GotoWebinar Campaign From Scratch

Instructions and best practices for [Mautic] campaigns and emails in a GoToWebinar campaign - from [Mautic Inc][mautic-inc-gotowebinar].

[mautic-inc-gotowebinar]: <https://mautic.com/help/create-gotowebinar-campaign-scratch/>

[cron]: <./../setup/cron_jobs.html>
[citrix-developer]: <https://goto-developer.logmeininc.com/user>
[GotoWebinar]: <https://www.gotomeeting.com/webinar>
