# FeatherTask
How to publish android app to the play store

# Generate key and build apk
Go to link to generate an upload key
https://facebook.github.io/react-native/docs/signed-apk-android.html

Generate upload key command on app
keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000

Copy the my-release-key.keystore file under the android/app directory

Edit the file  ~/.gradle/gradle.properties

MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
MYAPP_RELEASE_KEY_ALIAS=my-key-alias
MYAPP_RELEASE_STORE_PASSWORD=YOURCREATEDPASSWORD
MYAPP_RELEASE_KEY_PASSWORD=YOURCREATEDPASSWORD

Edit android/app/build.gradle file

android {
    ...
    defaultConfig { ... }
    signingConfigs {
        release {
            if (project.hasProperty('MYAPP_RELEASE_STORE_FILE')) {
                storeFile file(MYAPP_RELEASE_STORE_FILE)
                storePassword MYAPP_RELEASE_STORE_PASSWORD
                keyAlias MYAPP_RELEASE_KEY_ALIAS
                keyPassword MYAPP_RELEASE_KEY_PASSWORD
            }
        }
    }
    buildTypes {
        release {
            ...
            signingConfig signingConfigs.release
        }
    }
}

On your project terminal
cd android
mac
./gradlew bundleRelease
window
gradlew bundleRelease

upload file to playstore android/app/build/outputs/bundle/release/app.aab

# Create Your App
https://developer.android.com/distribute/console
sign in into your account

1. Click CREATE APPLICATION
2. Enter your title, click CREATE
3. Upload apk from /android/app/build/output/apk/release/app-release.apk
4. Fill in the fields with * and load images as needed
5. Save As Draft
6. Click on app release tab
# App release Tab
1. Click manage on production/ click CREATE RELEASE
2. Click continue on App signing Google play
3. Enter description in "What's new in this release?" inside the bracket.
4. Click Content Rating tab
# Content Rating
1. Fill in the fields with *
2. Select category and select the following.
3. Click save questionaire
4. Click calculate rating
5. Click Apply rating
6. Click Price & distribution tab
# Price & distribution
1. Select Available
2. Fill and check in the fields with *
3. Click save draft
3. Click App release tab
# App Release
1. Click Edit Release
2. Click Review
3. Click start rollout and confirm
