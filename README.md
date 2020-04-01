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
./gradlew assembleRelease
window
gradlew assembleRelease

# Create Your App
https://developer.android.com/distribute/console
sign in into your account

1. Click CREATE APPLICATION
2. Enter your title, click CREATE
3. Fill in the fields with *
