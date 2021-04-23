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
Beta deploy to testflight 
### ios ios_tesflight_without_build
```
fastlane ios ios_tesflight_without_build
```
Upload binary to testflight without build
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
Android build and release to beta via firebase
### android beta_crashlytic
```
fastlane android beta_crashlytic
```
Submit a new Beta Build to Crashlytics Beta
### android deploy_playstore
```
fastlane android deploy_playstore
```
Deploy a new version to Google PlayStore

----

This README.md is auto-generated and will be re-generated every time [fastlane](https://fastlane.tools) is run.
More information about fastlane can be found on [fastlane.tools](https://fastlane.tools).
The documentation of fastlane can be found on [docs.fastlane.tools](https://docs.fastlane.tools).
