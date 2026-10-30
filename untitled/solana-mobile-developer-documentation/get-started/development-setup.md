# Development Setup

This section covers the steps to:

* Set up your local environment for Android development.
* Configure a device or emulator for building apps for the dApp Store.
* Install an MWA-compliant wallet app for development purposes.

## Set up Android development environment

To build apps for the dApp Store, you need to setup your environment for Android development.

**Supported Frameworks**

* Expo / React Native
* Kotlin (Native)
* Flutter

For both Expo or React Native Android development: Expo’s system requirements are [Node.js (LTS)](https://nodejs.org/en/download) and a supported operating system: Linux, macOS, or Windows (PowerShell and WSL 2). View the Expo [**setup documentation**](https://docs.expo.dev/get-started/set-up-your-environment/?platform=android\&device=physical\&mode=development-build\&buildEnv=local) (Choose custom development build instead of Expo Go).

For Kotlin Android development: Install [Android Studio](https://developer.android.com/studio/install).

For Flutter Android development: View the official Flutter [**setup documentation**](https://docs.flutter.dev/platform-integration/android/setup).

## Setup Device/Emulator

You can test your app during development on any Android device or emulator. A Solana Mobile device is **not** required for dApp Store development—testing on a standard Android device is typically sufficient. For detailed device setup instructions, refer to Android’s official documentation:

## Setting up a physical device

## Configuring the Android Emulator

## Install a development wallet app

The [Mobile Wallet Adapter](mobile-wallet-adapter.md) (MWA) library allows your app to connect and interact with compatible wallet apps on your device. Install an MWA-compatible wallet app to test your app’s Mobile Wallet Adapter integration.

### Mock MWA Wallet

Solana Mobile provides a mock development wallet for you to test your app with and get a feel of what Seed Vault Wallet interactions on the Seeker will look like. The mock wallet features:

* Mobile Wallet Adapter support
* Simulate connection or signing errors

It is intended for development purposes only, so it does not store a persistent keypair and the wallet is reset each time the app is exited.

Installation:

{% stepper %}
{% step %}
## Clone the Mock MWA Wallet repo

Clone the Mock MWA Wallet repo from the [github repository](https://github.com/solana-mobile/mock-mwa-wallet).

```bash
git clone https://github.com/solana-mobile/mock-mwa-wallet.git
```
{% endstep %}

{% step %}
## Open the project in Android Studio

In Android Studio, `Open project > Navigate to the directory > Select mock-mwa-wallet/android/build.gradle`.
{% endstep %}

{% step %}
## Select the build configuration

After Android Studio finishes loading the project, select `fakewallet` in the build/run configuration dropdown in the top right.

![Mock MWA Wallet build](<../../.gitbook/assets/mock mwa wallet install.png>)
{% endstep %}

{% step %}
## Build and run the app

After it builds successfully, you should see the app on your connected Android device or emulator.
{% endstep %}
{% endstepper %}

### Other MWA-compliant wallet apps

You can also install and test with these popular MWA-compatible wallet apps:

![](https://www.solflare.com/favicon.ico)

## Solflare

![](https://jup.ag/favicon.ico)

## Jupiter Mobile

## Next steps

You have a development environment and testing device, and are now ready to start developing. Check out these links to quickly get an app running:

## Create a Project

## Sample Apps
