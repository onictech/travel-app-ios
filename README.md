Travelpayouts Travel App iOS
=================
[![Build Status](https://travis-ci.com/travelpayouts/travel-app-ios.svg?branch=master)](https://travis-ci.com/travelpayouts/travel-app-ios)
#### Руководство [по-русски](https://github.com/travelpayouts/travel-app-ios/blob/master/README_RU.md)
## Description
[Travelpayouts](https://www.travelpayouts.com) Travel App iOS is an app template for flights and hotels search. When your user books flight or hotel, you get paid. Aviasales, Jetradar and Hotellook official apps are based on the same code.

You can use this template as a base for you application, or you can use it as is changing only the main settings (app title, color scheme, icon, etc).

To track statistics and payments, please visit our affiliate network website — [Travelpayouts.com](https://www.travelpayouts.com/).

To learn more about the Travelpayouts affiliate network, please visit [Travelpayouts FAQ](https://support.travelpayouts.com/hc/en-us/articles/203955613-Commission-and-payments).

## <a name="usage"></a>How to build your own app using the template project
### 📲 Setup
1. Download the latest release of template project (not beta) here: [https://github.com/travelpayouts/travel-app-ios/releases](https://github.com/travelpayouts/travel-app-ios/releases), file Source Code (zip).
Alternatively you can clone the repository for development.
2. Dependencies are managed via CocoaPods (cocoapods.org). It can be installed via Bundler.
The following installation commands should be executed in the project folder (unpacked zip archive or cloned repository):
  ```bash
  sudo gem install bundler
  bundle install
  bundle exec pod install --repo-update
  ```
**Use the ```TravelpayoutsTravelApp.xcworkspace``` to work with your project**.

3. Add your partner's token and marker in ```TravelpayoutsTravelApp/default_config.plist``` file to parameters ```partner_marker``` and ```api_token```.
You can get the partner marker and API token on our website: [Travelpayouts](https://travelpayouts.com/).
4. AppStore app publishing requires unique app identifier (bundle id). It can be configured in Xcode.
![](https://github.com/travelpayouts/travel-app-ios/raw/master/readme_files/xcode_bundle_id.png)
5. Change app name in files ```Info.plist``` and ```LaunchScreen.xib```.
6. Use the ```default_config.plist``` config file to enable/disable flights/hotels tabs, to add app description, feedback email, app website link and App Store app link for the "About" page and to add localized values for external links.
7. Test the app on your iPhone/iPad or in Xcode simulator.
8. Publish the app via [App Store Connect](https://appstoreconnect.apple.com)

### 📱 iOS versions support
Application supports iOS 11.0 and higher

### 🖼 App Icon
**Do not forget to replace app icons** (Template project includes simple white icons by default). To do this you will need to replace icons in ```TravelpayoutsTravelApp/AppIcon.xcassets/AppIcon.appiconset``` folder (20.png, 29.png, 40.png etc) with your own icons with same names.

### ✈️🏨 Tab selection
1. If you want to remove flights or hotels search tab, change values of ```flights_enabled``` and ```hotels_enabled``` to NO in Project settings. Information tab can't be removed this way.
2. You can add Car Rental tab. To do this you need to join one car rental partner program from [Travelpayouts programs](https://www.travelpayouts.com/programs). Then you will need to generate a partner link and add it to the ```TravelpayoutsTravelApp/default_config.plist``` file to parameter ```car_rental_link```.

### 🔧🌻 Color customization
You can choose color scheme in ```ColorSchemeManager.swift``` file. Just add to ```current``` variable one of these values: BlackColorScheme() / PurpleColorScheme(). Or set CustomColorScheme() value and set up any color scheme you need in ```CustomColorScheme.swift``` file.
Here is a list of primary fields with explanations:

|Title|Description|
|--------|--------|
mainColor | Primary app color
actionColor | Actions highlight color

Fine-grained color customization can be configured in file ```ASTJRC.swift``` by overriding colors from the base class ```JRC```.

### 🔧📄 Text customization
You can change search forms titles in ```AppLocalizations.swift``` file. Uncomment and edit a variable to change corresponding search form title. Title can be localized in multuple languages if you use ```NSLocalizedString``` and add all localizations to ```Localizable.strings``` files.

### 🤑 Appodeal ads setup
To get additional profit from ads, we've integrated Mobile Ads [Appodeal SDK](https://www.appodeal.com/) in the app. To configure it, specify the ```appodeal_key``` parameter in the ```default_config.plist``` file (get your API key by registering at [Appodeal](https://www.appodeal.com/)). Ads will appear on the waiting screens for tickets and hotels searching by default.

### ⭐️ Feedback
Set up the ```feedback_email``` and ```itunes_link``` parameters in ```default_config.plist``` file to activate "Contact us" and "Rate this app" links.
The recommended format for ```itunes_link``` is the following: ```https://itunes.apple.com/app/id1234567890?action=write-review```, where ```id1234567890``` is the identifier of a published application.

## 🏭 **Use of Firebase**
Template app supports **Firebase** services. To enable them, please connect your app in the Firebase console, download and copy with replacement the ```GoogleService-Info.plist``` file to ```TravelpayoutsTravelApp``` folder and switch the ```firebase_enabled``` flag to ```YES``` in the ```default_config.plist``` file. Out of the box there is an analytics support for: Search / Ticket opened / Ticket booked in the airlines part and Search / Hotel opened / Hotel booked in the hotels part of the app.


Existing app integration
=================
[Travelpayouts](https://www.travelpayouts.com) Sample Flights App is an example of an existing iPhone/iPad app intergation with AviasalesKit library to add flights/hotels/car rental search. Users of your app will be able to book tickets or hotels and you will get paid.

To track statistics and payments, please visit our affiliate network website — [Travelpayouts.com](https://www.travelpayouts.com/).

To learn more about the Travelpayouts affiliate network, please visit [Travelpayouts FAQ](https://support.travelpayouts.com/hc/en-us/articles/203955613-Commission-and-payments).

## Library integration
App should support iOS 11 or newer as the minimum iOS version, and it should support Swift language. If your app is written in Objective-C you can wrap all library calls in a class which will be available in Objective-C.

### Add CocoaPods dependencies
Add the following function with dependencies to Podfile
```ruby
def aviasales_kit_dependencies
    pod 'AviasalesKit', podspec: 'https://ios.aviasales.ru/cocoapods/AviasalesKit_6.3.podspec'

    # forked AviasalesKit dependencies
    pod "CollectionSwipableCellExtension", git: 'https://github.com/KosyanMedia/CollectionSwipableCellExtension.git', commit: 'd3d7c9ee8721562174cbd2c89f88b1d05bbc5fc0'
    pod "SloppySwiper", git: 'https://github.com/glassoff/SloppySwiper.git', branch: 'aviasales'
    pod 'LDNetDiagnoService', git: 'https://github.com/KosyanMedia/LDNetDiagnoService_IOS.git', commit: '34eacdaa7767f95389b13998bef3fa9137edb2b1'
    pod 'libCurlPods', git: 'https://github.com/KosyanMedia/libCurlPods.git', tag: '7.60.3'
    pod 'MagicalRecord', git: 'https://github.com/magicalpanda/MagicalRecord.git', tag: 'v2.4.0'
    pod 'Neon', git: 'https://github.com/KosyanMedia/Neon.git', commit: '3f32f7a9276732dfa28c5e3886f2f95e76aa60c5', inhibit_warnings: true
    pod 'UIColor+Hex', git: 'https://github.com/KosyanMedia/UIColor-Hex.git', commit: 'df1248c06c11be7c67b7dd3227bff1113112e823'

    # suppress warnings
    pod 'TTTAttributedLabel', inhibit_warnings: true
    pod 'SwiftProtobuf', inhibit_warnings: true
    pod 'BZipCompression', inhibit_warnings: true
    pod 'FMDB', inhibit_warnings: true
    pod 'GRMustache', inhibit_warnings: true
    pod 'PromiseKit', inhibit_warnings: true
    pod 'COSTouchVisualizer', inhibit_warnings: true
end
```

In the target from which you want to launch the search screens call the dependencies function.
```ruby
target 'SampleFlightsApp' do
    aviasales_kit_dependencies
end
```

Install dependencies.
```sh
pod install --repo-update
```

### Library initialization
Add initialization code to your AppDelegate. Alternatively you can call this setup once before the first AviasalesViewControllersFactory invocation.
```swift
import ASTemplateConfiguration
```
```swift
AviasalesViewControllersFactory.shared.setup(window: window, config: { () -> Config in
    var colorParams = ColorParams()
    colorParams.mainColor = "9C6CBE" // primary style color (search form background)
    colorParams.actionColor = "CE0755" // secondary style color (search button)

    var config = Config()
    config.partnerMarker = "маркер" // partner marker https://travelpayouts.com/
    config.apiToken = "токен" // partner token https://travelpayouts.com/
    config.carRentalLink = "ссылка" // (optional) partner link to car rental https://www.travelpayouts.com/programs
    config.colorParams = colorParams
    return config
}())
```
Create required screens where you need them:
```swift
let flightsViewController = AviasalesViewControllersFactory.shared.flightsViewController()
let hotelsViewController = AviasalesViewControllersFactory.shared.hotelsViewController()
let carRentalViewController = AviasalesViewControllersFactory.shared.carRentalViewController()

viewController.present(flightsViewController, animated: true, completion: nil)
```

### info.plist changes
The library requires some changes in info.plist to work correctly:
```xml
<true/>
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
    <key>NSAllowsArbitraryLoadsInWebContent</key>
    <true/>
</dict>
<key>NSLocationWhenInUseUsageDescription</key>
<string>Used to find nearby hotels.</string>
```
NSAppTransportSecurity changes are required for some booking agencies. NSLocationWhenInUseUsageDescription is requred for nearest hotels search function.

### Fine tuning
You can configure some of the same settings as in the Travel App.
Colors can be configured the same way as in ```ASTJRC.swift```.
Search screen titles and some other texts can be configured the same way as in ```AppLocalizations.swift```.
