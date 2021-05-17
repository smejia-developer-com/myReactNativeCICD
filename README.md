# myReactNativeCICD

Enjoy this fast and furious tutorial about how to create a starter template of react-native APP and prepare a complete CI/CD to prepare our app and distribute as signed app to (Android)Playstore or Firebase Dist and (IOS)testflight automatically via github actions.

Complete tutorial on the following link:
https://my-reactnative-cicd-tutorial-website.s3.amazonaws.com/index.html


## Initial Setup :
We need to consider having installed Node , npm , xcode to run IOS apps and/or android  Studio to test android apps.

Well, let's create our CI/CD react app:

# IMPORTANT # :
OH YOU CAN AVOID doing the Step 1-4 just cloning this ready-to-go starterReactNativeKit repo doing a git clone https://github.com/smejia-developer-com/myReactNativeCICD as you will get a simpleReactApp + CICD files ready to be changed with your own information.


-------------------------- If you want to create a ReactApp from scratch ------------

### Step 1: Create a empty react-native project running the following on the terminal:

```
npx react-native init MyReactCICDApp
```


On this point we should be able to run our first hello-world react app running:

### Step 2: Start our App 
```
npx react-native start
```


### Step 3: Run IOS app locally
```
npx react-native run-ios
```


Congrats! You've successfully run and modified your first React Native app.


------------------  ReactNative CICD info below ------------------

### Step 4: Lets prepare our CI/CD pipeline to deploy our react app in Testflight (IOS) or googlePlay (Android)





fastlane documentation
================
# Installation

Make sure you have the latest version of the Xcode command line tools installed:

```
xcode-select --install
```

Install _fastlane_ using
```
[sudo] gem install fastlane -NV
```
or alternatively using `brew install fastlane`


Navigate your terminal to your project's directory and run
```

fastlane init
```

In order to get working the android fastlane CICD we should install the following plugins (on the root of the project):
fastlane add_plugin firebase_app_distribution
fastlane add_plugin increment_version_code

AND FINALLY WE SHOULD CONFIGURE, GENERATE OUR KEYSTORE AND APPLE APP INFO Before running any CD job from fastlane or github actions.

Very useful Android CICD tutorial to configure any extra details about android playstore config, keystore steps and GCP key.json key to connect to playstore and more:

https://www.raywenderlich.com/10187451-fastlane-tutorial-for-android-getting-started


Very useful IOS tutorial to configure our IOS CICD options about Apple store, itunes connect, sign and so on:

https://www.gitstart.com/post/automatic-deployment-of-react-native-ios-apps-with-fastlane-and-github-actions

For now I can show you all the github actions available here and each fastlane related to ReactNative CICD:


# Available Actions
## iOS
### ios build_only_ios
```
fastlane ios build_only_ios
```
Clean and Build IOS only
### ios ios_build_with_match
```
fastlane ios ios_build_with_match
```
Create Signed IPA Build
### ios ios_beta_tesflight
```
fastlane ios ios_beta_tesflight
```
Clean- Build - Sign and Distribute a new Beta testing App directly to AppleStore - testflight section 
### ios ios_tesflight_without_build
```
fastlane ios ios_tesflight_without_build
```
Try to Upload a fake binary to testflight without build in order to test your configuration on upload_testflight step. Very useful to avoid 2FA and lossing minutes on github actions
### ios ios_ci_tests
```
fastlane ios ios_ci_tests
```


----

## Android
### android run_test_only
```
fastlane android run_test_only
```
Runs all the tests
### android build_as_debug
```
fastlane android build_as_debug
```
Android build as debug
### android build_as_release
```
fastlane android build_as_release
```
Android build as release
### android firebase_deploy
```
fastlane android firebase_deploy
```
Android build and distribute as alpha version via firebase App Distribution
### android beta_crashlytic
```
fastlane android beta_crashlytic
```
Submit a new Beta Build to Crashlytics
### android deploy_playstore
```
fastlane android deploy_playstore
```
Deploy a new version android BETA testing build directly to Google PlayStore

----

This README.md is auto-generated and will be re-generated every time [fastlane](https://fastlane.tools) is run.
More information about fastlane can be found on [fastlane.tools](https://fastlane.tools).
The documentation of fastlane can be found on [docs.fastlane.tools](https://docs.fastlane.tools).


Contributing
This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app). And based on very useful tutorials about ANDROID AND IOS config details (Android): https://www.raywenderlich.com/10187451-fastlane-tutorial-for-android-getting-started and IOS: https://www.gitstart.com/post/automatic-deployment-of-react-native-ios-apps-with-fastlane-and-github-actions)

