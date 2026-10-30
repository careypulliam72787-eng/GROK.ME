# Publishing from Google Play to the dApp Store

Learn how to publish your existing Google Play app to the dApp Store.

## Overview

Publishing your existing Google Play app to the dApp Store requires:

1. A release APK file signed with a **new, unique signing key** (different from Google Play)
2. Following the standard dApp Store publishing workflow

Key differences from Google Play:

* **File Format**: dApp Store submission requires APK files (Google Play uses AAB)
* **Signing Key**: Must use a completely separate signing key from Google Play
* **In-App Purchases**: No 30% tax on in-app purchases or transactions

{% hint style="danger" %}
**CRITICAL REQUIREMENT**: You cannot use the same signing key for both Google Play and the dApp Store.
{% endhint %}

## Build Your APK

{% stepper %}
{% step %}
### Create New Signing Key

Generate a new signing key exclusively for the dApp Store:

```bash
keytool -genkey -v -keystore dappstore.keystore \
  -alias dappstore \
  -keyalg RSA \
  -keysize 2048 \
  -validity 10000
```

**Store the keystore file and passwords securely** - losing them means you cannot update your app. For reference, view the [Android app signing guide](https://developer.android.com/studio/publish/app-signing).
{% endstep %}

{% step %}
### Build Signed APK

{% tabs %}
{% tab title="Native Android" %}
Configure dual-store setup in `app/build.gradle` using product flavors:

```groovy
android {
    signingConfigs {
        // Existing Google Play signing config
        googlePlay {
            storeFile file("keystores/googleplay.keystore")
            storePassword "your_googleplay_keystore_password"
            keyAlias "googleplay"
            keyPassword "your_googleplay_key_password"
        }

        // dApp Store signing config
        dappStore {
            storeFile file("keystores/dappstore.keystore")
            storePassword "your_dappstore_keystore_password"
            keyAlias "dappstore"
            keyPassword "your_dappstore_key_password"
        }
    }

    flavorDimensions = ['store']

    productFlavors {
        googlePlay {
            dimension 'store'
        }

        dappStore {
            dimension 'store'
        }
    }

    buildTypes {
        release {
            // Assign signing configs to each flavor
            productFlavors.googlePlay.signingConfig signingConfigs.googlePlay
            productFlavors.dappStore.signingConfig signingConfigs.dappStore
        }
    }
}
```

Build the dApp Store APK:

```bash
./gradlew assembleDappStoreRelease
```

Alternatively, build using Android Studio IDE: **Build** → **Select Build Variant** → **dappStoreRelease** → **Build APK**.

Your dApp Store APK will be at `app/build/outputs/apk/dappStore/release/app-dappStore-release.apk`

For reference, view the [Android signing documentation](https://developer.android.com/studio/publish/app-signing#gradle-sign).
{% endtab %}

{% tab title="Expo" %}
Configure `eas.json` with local credentials for dApp Store builds:

```json
{
  "build": {
    "dapp-store-production": {
      "android": {
        "buildType": "apk",
        "credentialsSource": "local"
      }
    }
  }
}
```

Create `credentials.json` with your dApp Store keystore details:

```json
{
  "android": {
    "keystore": {
      "keystorePath": "./dappstore.keystore",
      "keystorePassword": "your-keystore-password",
      "keyAlias": "dappstore",
      "keyPassword": "your-key-password"
    }
  }
}
```

{% hint style="warning" %}
**Security** Store `credentials.json` securely and add it to `.gitignore` to prevent accidental commits to source control.
{% endhint %}

{% tabs %}
{% tab title="EAS Build (Cloud)" %}
Build the dApp Store APK in the cloud using local credentials:

```bash
eas build --platform android --profile dapp-store-production
```
{% endtab %}

{% tab title="Local Build" %}
Build the dApp Store APK entirely on your machine using local credentials:

```bash
eas build --platform android --profile dapp-store-production --local
```
{% endtab %}
{% endtabs %}

This approach lets you use EAS-managed credentials for Google Play and local credentials for the dApp Store.

For reference, view the Expo [local credentials documentation](https://docs.expo.dev/app-signing/local-credentials/#credentialsjson).
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Verify APK

Confirm your APK is properly signed before submission:

```bash
apksigner verify --print-certs app-release.apk
```

For reference, view the [apksigner documentation](https://developer.android.com/studio/command-line/apksigner#usage-verify).
{% endstep %}
{% endstepper %}

## Next Steps

With your signed APK ready, follow the standard dApp Store publishing process and [Submit your app](submit-a-new-app.md)

## Additional Resources

* [Publisher Policy](solana-mobile-publisher-policy.md) - Review dApp Store requirements
* [Support](get-support.md) - Get help with publishing issues
