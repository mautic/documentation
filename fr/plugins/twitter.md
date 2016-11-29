# Mautic - Twitter plugin

This plugin can:

- display the tweets for a contact with valid Twitter handle,
- load additional information from the Twitter profile,
- place a share button to the landing pages.

### Requirements

- Mautic installed on a publicly accessible URL. This plugin won't work on a localhost because callbacks from Twitter to Mautic are necessary.

### Authorize the plugin

A Twitter application has to be created for authorization. To create/manage one, go to [apps.twitter.com](https://apps.twitter.com/). While creating your Twitter app, you'll have to insert a *Callback URL*. This callback URL is written in the Twitter plugin configuration.

When your Twitter app is created, copy the *API Key* to the *Client Key* field in Mautic's Twitter configuration and *API Secret* to *Client Secret* field. Click the *Authorize* button. 

Don't forget to switch *Published* to *Yes* and save the configuration.

### Configure the plugin

If your Twitter plugin is authorized correctly, you can configure the *Features* and *Contact Field Mapping* tab in the plugin configuration. The *Features* tab is self-explanatory. The fields like *Tweet text*, *Via*, *Recommended* and *Hashtag* are prepared there for future implementation with Twitter. Read here how to configure the *[Contact Field Mapping](./../plugins/field_mapping.html)*. If you don't have a special field for Twitter handle yet, create it in the Contact Field section.

The tweets of a contact should appear on the contact's profile as soon as the Twitter handle contact field is filled with an existing Twitter handle.

Use `{sharebuttons}` token in the Mautic Landing Pages in the place where you want to display the share buttons.

### Twitter API limitations

The original idea was that Mautic will search for additional information about a contact in various social platforms. But since the time the social plugins were written, social platforms restricted the API search to only the username.
