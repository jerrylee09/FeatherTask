# FeatherTask
How to publish android app to the play store

Go to link to generate an upload key
https://facebook.github.io/react-native/docs/signed-apk-android.html

Generate upload key command on app
keytool -genkeypair -v -keystore my-upload-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000

/usr/libexec/java_home
