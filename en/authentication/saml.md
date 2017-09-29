# SAML Single Sign On

SAML is a single sign on protocol that allows single sign on and user creation in Mautic using a 3rd party user source called an identity provider (IDP).

## Enabling SAML 

To enable SAML support in Mautic, you first need the IDP's metadata xml. This will be provided to you by the IDP. If it is a URL, browse to the URL then save the content into an xml file. 

Go to Configuration -> User/Authentication Settings. Then upload this file as the `Identity provider metadata file`. 

It is recommended that a non-admin role be created to use as the default role for created users. Select this role in the `Default role for created users` dropdown.

## Configuring the IDP

The IDP may ask for the following settings:

1) `Entity ID` - this will be site URL and is displayed at the top of User/Authentication Settings. Copy this exactly as is to the IDP.

2) `Service provider metadata` - if a URL is requested, use `https://your-mautic.com/saml/metadata.xml`. If a file, then browse to that URL and save the content as an XML file.
 
3) `Assertion consumer service` - Use `https://your-mautic.com/s/saml/login_check`

4) `Issuer` - this should be provided by the IDP but is often configurable. If it is a URL, be sure that the scheme (http:// and https://) are not part of it.

5) `Verify request signatures` or a SSL certificate - If the IDP supports encrypting and validating request signatures from Mautic to the IDP, generate a self signed SSL certificate. Upload the certificate and private key through Mautic's Configuration ->  User/Authentication Settings under the `Use a custom X.509 certificate and private key to secure communication between Mautic and the IDP.` section. Then upload the certificate to the IDP.

6) `Custom attributes` - Mautic requires 3 custom attributes that must be included in the IDP responses for the user email, first name and last name. Username is also supported but is optional. Configure the attribute names used by the IDP in Mautic's Configuration ->  User/Authentication Settings under the `Enter the names of the attributes the configured IDP uses for the following Mautic user fields.` section.

## Logging In
Once Mautic is configured with the IDP and the IDP with Mautic, Mautic will by default redirect logins to the IDP's login page. `/s/login` is still available for direct logins but will need to be browsed to directly.

Login to the IDP where you'll be redirected back to Mautic. If the exchange is successful, the user will be created, if it does not already exist, and logged in.

## Disable SAML
To disable SAML, simply click the `Remove` link to the right of the `Identity provider metadata file` label.  

![](/authentication/media/saml.png)