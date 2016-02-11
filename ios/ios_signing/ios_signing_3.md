# Step 2: App IDs

## What is an App ID?

An App ID is used to identify your application and must be specified in order to sign and publish your application. The App ID protects your application as it is unique.

If an attacker tries to replace your Store version with his he will then have to build an app with the exact same ID meaning that he will also have to find and use the certificate, and provisioning profile attributed to this ID.

## How to generate an app ID

- Go to **App IDs > '+'**.
- Give your ID a name
- Select **Explicit App ID**
- The ID correspond to the following format **org.example.myproject(.subproject)**


## Managing IDs and Environments

Let's say you have 3 environments: *development, integration and production*. Using the same ID will cause the existing version to be overwritten and will likely waste your time. If you want to be able to test the three environments on the same phone you will have to setup 3 different IDs in order to keep each version on your phone.

Another way of doing this (but please keep an explicit ID for your production environment) is to use a **Wildcard ID**. The format to be used is **org.example.myproject.***. This will allow you to setup any number of environment as necessary.

So in our case we would use:
- *org.example.myproject.development* => *Wildcard ID*
- *org.example.myproject.integration* => *Wildcard ID*
- *org.example.myproject* => *Explicit ID* (For the Store)
