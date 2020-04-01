# FeatherTask
How to publish android app to the play store

# Generate key and build apk
Go to link to generate an upload key
https://facebook.github.io/react-native/docs/signed-apk-android.html

Generate upload key command on app
keytool -genkeypair -v -keystore my-upload-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000

copy my-upload-key.keystone to /android/app/

cd android
./gradlew bundleRelease

# Create Your App
https://developer.android.com/distribute/console
sign in into your account

1. Click CREATE APPLICATION
2. Enter your title, click CREATE
3. Fill in the fields with *
