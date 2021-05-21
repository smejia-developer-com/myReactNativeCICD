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

### Configure Android CICD Details:
On this step we should configure any extra details about firebase app distribution configuration and Google playStore config, keystore.
 Firebase App Distribution (Configuration Steps):
 
Step4.1: Open Firebase Console page (Visit the Firebase website)
Step4.2: Create a new firebase project (Select Android app Icon and follow the steps)
Step4.3: Add Firebase to your Android app ( set your android package name).
Step4.4: Follow the instructions to add google-services.json  into your android project.
Step4.5: Add the Firebase SDK into our project file called: “build.gradle” 
Once installed, open the General Settings page for the project. Scroll down to the Your apps section 
and get the AppID to be saved into your github action secrets(explained later).
Step4.6: Add testing group and add testers emails

And we should be all set on firebase.
More details on this great android fastlane tutorial:

https://www.raywenderlich.com/10187451-fastlane-tutorial-for-android-getting-started#toc-anchor-013

Creating PlayStore Credentials (Configuration Steps):
Step4.7: Go to  Google Play Console (We assume that you already create a google developer account.
Step4.8: Click Settings and then click API access
Step4.9: Click the CREATE SERVICE ACCOUNT 
Step4.10 Provide a custom Service account name 
Step4.11 Choose role as Service Account User
Step4.12 Download the json config file.
Step4.13 Click the Grant Access  button on your new service created
Step4.14 Choose Release Manager role
Step4.15 Click ADD USER button to complete the steps and you are all set!

More details on this great android fastlane tutorial:

https://www.raywenderlich.com/10187451-fastlane-tutorial-for-android-getting-started#toc-anchor-018


### Configure IOS CICD Details:

On this part we should configure our AppleStore and AppleConnect section to upload our IOS build directly to testflight. Also authenticating apple developer account and github account to use match signing process.

Step5.1>  Setup Match locally ( https://docs.fastlane.tools/actions/match/)
Step5.2> Create a new, shared Apple developer account (this will be used by our CICD)
Step5.3> Create a Private Github Repository (To be used via match to save our provision Profiles and Apple IOS certificates).
Step5.4> Then run fastlane match development in your local machine and follow the steps.
Then do the same for the other methods(such as: ad-hoc and appstore).
(This fastlane match process should automatically set up all certificates, profiles and push to the remote repository).
At the end of all these steps our github actions will be able to run the fastlane to push the sign and push the IOS build from a virtual machine.


For more details about these config I suggest using the great IOS fastlane tutorials to configure our IOS CICD options about Apple store, itunes connect, sign and so on:
https://www.gitstart.com/post/automatic-deployment-of-react-native-ios-apps-with-fastlane-and-github-actions
https://www.youtube.com/watch?v=Edr88s5YlH4
https://medium.com/@danielvivek2006/setup-fastlane-match-for-ios-6260758a9a4e




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
This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app). And based on very useful tutorials about ANDROID AND IOS config details (Android): https://www.raywenderlich.com/10187451-fastlane-tutorial-for-android-getting-started and IOS: https://www.gitstart.com/post/automatic-deployment-of-react-native-ios-apps-with-fastlane-and-github-actions
https://www.youtube.com/watch?v=Edr88s5YlH4, https://medium.com/@danielvivek2006/setup-fastlane-match-for-ios-6260758a9a4e
. Thanks everyone!

