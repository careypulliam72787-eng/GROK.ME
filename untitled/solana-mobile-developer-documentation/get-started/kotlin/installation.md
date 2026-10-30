# Installation

Add the core Solana Kotlin libraries to your Android project.

## Prerequisites

* Download [Android Studio](https://developer.android.com/studio) for development and device management.
* Follow the [Development Setup](../development-setup.md) guide to set up your [Android Device/Emulator](../development-setup.md#setup-deviceemulator) and install an MWA-compatible wallet.

## Add Gradle dependencies

In Android Studio, navigate to your Android project’s module `build.gradle.kts` file and add the following dependencies:

{% code title="build.gradle.kts" %}
```kotlin
dependencies {
    implementation("com.solanamobile:mobile-wallet-adapter-clientlib-ktx:2.0.3")
    implementation("com.solanamobile:web3-solana:0.2.5")
    implementation("com.solanamobile:rpc-core:0.2.7")
    implementation("io.github.funkatronics:multimult:0.2.3")
}
```
{% endcode %}

### Overview of each dependency

* `com.solanamobile:mobile-wallet-adapter-clientlib-ktx`: Mobile Wallet Adapter client library for interacting with MWA-compatible wallets.
* `com.solanamobile:web3-solana`: Solana Kotlin library providing core Solana primitives like transaction building and public key class.
* `com.solanamobile:rpc-core`: A Kotlin library providing a generic interface and abstractions for building Solana RPC requests.
* `io.github.funkatronics:multimult`: Lightweight utility library for Base58 conversions.

Build and run your app to verify the dependencies resolve correctly.

## Next steps

## Setup

Instantiate the MobileWalletAdapter client and connect to wallets.
