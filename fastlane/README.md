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
or alternatively using `brew cask install fastlane`

# Available Actions
## Android
### android unit_test
```
fastlane android unit_test
```
Gradle Unit Test
### android SCA
```
fastlane android SCA
```
Gradle Static Code Analysis
### android build
```
fastlane android build
```
Build New Version
### android code_coverage
```
fastlane android code_coverage
```
Code Coverage
### android upload_to_appcenter
```
fastlane android upload_to_appcenter
```


----

This README.md is auto-generated and will be re-generated every time [fastlane](https://fastlane.tools) is run.
More information about fastlane can be found on [fastlane.tools](https://fastlane.tools).
The documentation of fastlane can be found on [docs.fastlane.tools](https://docs.fastlane.tools).
