# Deploy a new Cordova app to Testflight in 5 minutes with Fastlane

Requirements:
- you have some prior knowledge about [codesigning an iOS app](../ios/ios_signing/ios_signing_1.md)
- you have an Apple developer account, enrolled in the Developer program (you have access to iTunes Connect)
- you have Fastlane installed (see [this tutorial](./fastlane_1_intro.md) to get started quickly)

First make sure the folder `platforms/ios` is present.
If not, run:
```shell
cordova platform add ios
```

At the root of the project create a `fastlane` folder and generate an `Appfile` and a `Fastfile`:
```shell
mkdir fastlane
touch fastlane/Appfile fastlane/Fastfile
```

Then fill in the Appfile and the Fastfile with your info, like this:

### Appfile

```Ruby

app_identifier "REPLACE_ME" # The bundle identifier of your app from your config.xml
apple_id "REPLACE_ME" # Your Apple email address
team_name "REPLACE_ME"  # Developer Portal Team name
itc_team_name "REPLACE_ME"  # iTunes Connect Team name

# you can even provide different app identifiers, Apple IDs and team names per lane:
# More information: https://github.com/fastlane/fastlane/blob/master/fastlane/docs/Appfile.md
```

### Fastfile

```ruby
default_platform :ios

platform :ios do
  # CHANGE the app name to the name of your app
  app_name = "MyAwesomeApp"
  # CHANGE xcodeproj to the path to your xcodeproj
  xcodeproj = "./platforms/ios/#{app_name}.xcodeproj"

  def cordova
    sh "cordova build --release --device"
  end

  desc "Create an app identifier on the developer member center and iTunes Connect"
  lane :produce do
    produce(app_name: app_name)
  end

  desc "Codesign, Archive and upload the app to Testflight"
  lane :testflight do
    # Get certificate
    cert

    # Get provisioning profile
    sigh

    # Handle config.xml and JS changes
    cordova

    # Recreate schemes to ensure a smooth transition from cordova to gym
    recreate_schemes(project: xcodeproj)

    # Archive app into ipa
    gym(scheme: app_name, project: xcodeproj)

    # Upload to Testflight
    pilot(distribute_external: false)
  end
end
```

You can check a real example of an `Appfile` and a `Fastfile` [here](https://gist.github.com/Almouro/e7ddd1c8080d2517248e2085f9c331a2).

Run `fastlane produce` to create it on the Apple developer center and iTunes Connect.

Now run `fastlane testflight` and let it build and upload to Testflight!
