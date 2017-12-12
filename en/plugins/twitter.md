# Mautic - Twitter plugin

This plugin can:

- send a personalized tweet to a contact
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

### View contact's tweet

When you have the Twitter plugin authorized and configured, you will be able to see contact's tweet history in the contact's detail page. But it will work only for contacts which have the Twitter handle (username) filled in their profile. See the limitations section below for more about that.

### Tweet to a contact

It's possible to tweet to a contact from a campaign. Either there is the special "Tweet contact" action where you can select the tweet which should be tweeted or you can use Marketing Messages Tweet channel to do the same thing.

The tweets can be tailored to the contact with tokens:
- `{twitter_handle}` will be replaced with Twitter Handle (username) from the contact's profile and so the contact will get Twitter notification about the mention.
- `{assetlink=2}` will insert a link to the Asset with ID 2.
- `{pagelink=1}` will insert a link to the Landing Page with ID 1.
All these tokens are easily accessible in the UI, so you can just click a button or select the Asset/Landing Page you wish to include to the tweet.

### Twitter API limitations

The original idea was that Mautic will search for additional information about a contact in various social platforms. But since the time the social plugins were written, social platforms restricted the API search only to the username.
