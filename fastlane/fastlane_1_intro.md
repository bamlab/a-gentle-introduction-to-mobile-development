# How to get started with Fastlane

Requirements:
- you have some prior knowledge about [codesigning an iOS app](../ios/ios_signing/ios_signing_1.md)
- you have an Apple developer account, enrolled in the Developer program (you have access to iTunes Connect)

Codesigning and deploying an app to the Apple Store is a fastidious, time-consuming, error-prone process.
See [this entry in Stack-Overflow](http://stackoverflow.com/questions/21250510/generate-pem-file-used-to-setup-apple-push-notification) just to get an idea. ;)

Don't worry, here comes [Fastlane](https://fastlane.tools/)!

![Fastlane](https://raw.githubusercontent.com/fastlane/fastlane/master/fastlane/assets/fastlane_text.png)

Fastlane is a toolbox (written in Ruby) that will allow you to automate all these tedious process.

## Install it

Install it with:
```shell
gem install fastlane
```
Don't worry if it takes a few minutes. A lot of goodness is installing.

## Try it out

You now have access to a lot of tools, called **actions**.
An **action** is designed to help you automate a single task.

For instance, let's try the action `cert`.
Run anywhere in a terminal:
```shell
$ cert
```

You will be prompted for your *Apple Id* and *password*.
Fastlane will use its [credentials manager](https://github.com/fastlane/fastlane/tree/master/credentials_manager) to store it in your keychain.

Yes. `cert` is automatically checking installed certificates on your machine
and creating one if it couldn't find any.

Now try to run:
```shell
sigh
```

You will be asked for a *bundle identifier*. Try to give one you've already used.
Yes. `sigh` is automatically creating/downloading provisioning profiles from your
developer account for the specified app.

#### There is a lot of useful actions bundled up in Fastlane.

`produce` is used to create an *App Id* in the developer member cender and/or iTunes Connect.  
`cert` is used to create *certificates*.  
`sigh` is used to manage *provisioning profiles*  
`gym` is used to *build and archive your app*.  
`pilot` is used to upload an ipa to *testflight*  
`deliver` is used to manage the metadata on iTunes Connect.  
`pem` is used to manage your *push notification profiles*

And there are many more! You'll see them all if you run:

```shell
fastlane actions
```
If want to know more about a specific action, you can run:
```shell
fastlane actions [action]
```
or you can [check the docs](https://github.com/fastlane/fastlane/blob/master/fastlane/docs/Actions.md).

## Orchestrate the magic in lanes

Now, what you'd probably want to do is put some of these actions together in a process.

For instance, to deploy an app to Testflight from scratch, you'd need to have a certificate, a provisioning profile. Then you'd archive your app and finally you'd upload it to Testflight.  
Your process would be `cert`, `sigh`, `gym` and then `pilot`.

Well, with Fastlane, you can put actions together in a **lane**.
In a folder where you have an **Xcode project**, run:
```shell
$ fastlane init
```
It will create your app on the Apple developer portal and on iTunes Connect, **automatically**! It is actually using the action `produce` to do so.
It will also generate a `fastlane` folder with an `Appfile` and a `Fastfile`.

The `Appfile` stores useful information that are used across all `fastlane` tools like your *Apple ID* or the application *Bundle Identifier*, to deploy your lanes faster and tailored on your project needs.
Find out more in [the docs](https://github.com/fastlane/fastlane/blob/master/fastlane/docs/Appfile.md)

In the `Fastfile`, you can create **lanes**, to orchestrate all the **actions** you'd want to use.

For instance, you could define:

```ruby
lane :beta do
  # Put any actions you'd want here, for instance:
  # Use cert to generate a certificate
  cert
  # Use sigh to download or generate a provisioning profile
  sigh
  # Use gym to archive your app
  gym
  # Use pilot to upload your app to testflight
  pilot(distribute_external: false)
end
```

Then run
```shell
$ fastlane beta
```
and let the magic happen!

## Where to go from here

See [this tutorial](./fastlane_2_cordova.md) to know how to use Cordova with Fastlane.
