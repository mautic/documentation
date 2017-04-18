# Citrix Plugins

## Description:
Create a plugin that pulls data from Mautic and pushes data to Mautic from GotoMeeeting, GotoWebinar, GotoTraining and GoToAssist) .
## Required Features:
1. Create registrants in GoToWebinar and GoToTraining based on campaign decisions, contact data and also from registration forms in Mautic
2. Pull back from registrant and attendee info into segments and campaigns  
3. Display webinar and training attendance as an additional activity on the contact timeline
4. Send emails with buttons to start GoToMeeting, GoToTraining and GoToAssist sessions

## Instructions
1. Enable the plugins you need

![image](https://cloud.githubusercontent.com/assets/2924026/19797584/54467954-9ca9-11e6-8e31-f80f7469fe84.png)

2. Activate the plugins with the Citrix Developer API keys

![image](https://cloud.githubusercontent.com/assets/2924026/19797588/5c6ce640-9ca9-11e6-981c-a98a728e1712.png)

3. Use the Consumer Keys from the developer website

![image](https://cloud.githubusercontent.com/assets/2924026/19797595/612744f0-9ca9-11e6-90b0-566fdff69ef4.png)

4. New segment filters will be available

![image](https://cloud.githubusercontent.com/assets/2924026/19797599/655fb6ce-9ca9-11e6-9d27-9ec295068a1a.png)

5. Past sessions will be available to choose from

![image](https://cloud.githubusercontent.com/assets/2924026/19797600/69dd3604-9ca9-11e6-8212-7a0a383bff34.png)

6. New fields will be availabe for forms

![image](https://cloud.githubusercontent.com/assets/2924026/19798154/9954bf30-9cac-11e6-8173-06acc0ca1fa1.png)

7. The fields will display the available events for each product (the form will validate that the mandatory fields are present)

![image](https://cloud.githubusercontent.com/assets/2924026/19797605/72ec51e4-9ca9-11e6-8416-be31a013c8d1.png)

8. Form actions will also be available

![image](https://cloud.githubusercontent.com/assets/2924026/19797611/7699f9c2-9ca9-11e6-96f5-d90dcafcbd3f.png)

9. Each action will permit to select a single event or let the user select from the form. They also include fields to map to obligatory lead fields

![image](https://cloud.githubusercontent.com/assets/2924026/19797613/7b25eb68-9ca9-11e6-99c7-d9f4053136ac.png)

10. This is an example of a form that lets the user select the event from a list

![image](https://cloud.githubusercontent.com/assets/2924026/19797614/7eea2f02-9ca9-11e6-86dd-c895bb0d65c3.png)

11. The Send Link actions require an email object with a Token to insert the link of the event (the available tokens are shown)

![image](https://cloud.githubusercontent.com/assets/2924026/19797615/82b326f2-9ca9-11e6-9d30-1324b7efd49a.png)

12. There are also conditions for campaigns (registered and attended)

![image](https://cloud.githubusercontent.com/assets/2924026/19797618/8693fb8e-9ca9-11e6-8ae2-44b67f05769e.png)

13. The campaign actions allow to select the event and the email template to send (if applicable)

![image](https://cloud.githubusercontent.com/assets/2924026/19797619/8a501b68-9ca9-11e6-8232-d5c23b9cf445.png)

14. This is an example of a campaign that sends a link to a preliminary meeting after a contact is identified as to have registered to a webinar (using segment)

![image](https://cloud.githubusercontent.com/assets/2924026/19797623/8d7b1252-9ca9-11e6-9370-b3f05cc08ee1.png)

15. In this example, the form has been submitted

![image](https://cloud.githubusercontent.com/assets/2924026/19797632/9122e614-9ca9-11e6-991c-70b2033ea6c9.png)

16. The new events appear in the contact's timeline

![image](https://cloud.githubusercontent.com/assets/2924026/19797638/9484bb7a-9ca9-11e6-9a18-62eab010378e.png)

17. The email with the link (that was injected with the Token) is viewed in the browser

![image](https://cloud.githubusercontent.com/assets/2924026/19797642/986c9c30-9ca9-11e6-9233-5e826f2520b9.png)

18. When the contact clicks on the link, it redirects to GoToMeeting to start the meeting

![image](https://cloud.githubusercontent.com/assets/2924026/19797644/9c6e43ce-9ca9-11e6-8f45-ec36b19502fa.png)

19. This is an example of a webinar where the contact attended

![image](https://cloud.githubusercontent.com/assets/2924026/19797647/a012bfb4-9ca9-11e6-8d27-92edfb071bfb.png)

20. When the crontab job that synchronizes the data runs, it retrieves the new state of the contact and it's visible on the timeline as an attended event

![image](https://cloud.githubusercontent.com/assets/2924026/19797652/a435ee36-9ca9-11e6-9936-17cd19384452.png)

#### The previous examples used GoToMeeting and GoToWebinar, but it's the same for GoToTraining and GoToAssist

### Other details
The cron job to synchronize the events is

    php app/console mautic:citrix:sync

    Usage:
        mautic:citrix:sync [options]

    Options:
        -p, --product[=PRODUCT]  Product to sync (webinar, meeting, training, assist)
        -i, --id[=ID]            The id of an individual registration to sync

### Update: Join GoToWebinar Button Token
1. Follow these steps to include a Join GoToWebinar button in a segment email:

2. Create a webinar in the [GotoWebinar website](https://www.gotomeeting.com/webinar)

3. Create a new contact and use the emaill address to register for the new webinar

4. Run the Citrix Sync command: `php app/console mautic:citrix:sync` so that the webinar information is retrieved to the database.

5. Create a segment with a "Webinar (registered)" filter. (Note that this is mandatory, and it will be validated when trying to save the email with the token in the body)
![image](https://cloud.githubusercontent.com/assets/2924026/24730532/5ff1f31e-1a21-11e7-9e5f-fbdc604c0883.png)

6. Add the contact to the segment manually or by running `php app/console mautic:segments:update`

7. Create a new segment email and assign the previously created segment.
![image](https://cloud.githubusercontent.com/assets/2924026/24730574/95b6083c-1a21-11e7-8c79-a8b9c45ab810.png)

8. Open the email builder and insert the GotoWebinar button token:
![image](https://cloud.githubusercontent.com/assets/2924026/24730644/0f294076-1a22-11e7-9af8-edd359587a41.png)

9. Send the email to the segment contacts.
![image](https://cloud.githubusercontent.com/assets/2924026/24730930/ddef679a-1a23-11e7-9610-513a44bcfd48.png)

10. The email in the new contact inbox should include a button to join the webinar with the appropiate URL for the contact.
![image](https://cloud.githubusercontent.com/assets/2924026/24731148/72272370-1a25-11e7-97ac-e04943f25775.png)

11. The button can be styled by overriding the `citrix-start-button` CSS class.
