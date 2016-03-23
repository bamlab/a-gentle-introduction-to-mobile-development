# Apple Certificates and Provisioning Profiles

***Problem:*** How do you sign your iOS application for production?

In the following chapter we will consider that you already own a valid Apple Developer account.

## What are certificates?

Apple Certificates are keys allowing you to sign your application for release. It is used by to verify that the person who is trying to publish a version of the application is its owner and the owner of the provisioning profile.

## What are provisioning profiles?

A provisioning profile is the key used to sign your application. It is linked to the application id to prevent using your certificate to sign something else than your application. The provisioning profile can also include some permissions required to access certain tools such as the push notifications.

## A bit about security

Both certificates and provisioning profiles exist to enforce security and ownership of every application available on the Apple Store. While the Provisioning Profile can be committed without any worries, it is utterly important to ensure that the certificates are stored in a safe location and shared only with the core members of your team.

Having your certificate and provisioning profile stolen can lead to someone stealing your identity and publishing an application which will be regarded by the Apple Store as yours.
