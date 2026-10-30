# MWA for Web Apps

## Overview

Mobile Wallet Adapter enables **Mobile Web Apps**, including PWAs, to connect locally to wallet apps on the same Android device.

## SDK

Use the **Mobile Wallet Standard** library to register MWA as a wallet option in your web app. It is compatible with any web app using the `@anza/wallet-adapter` libraries.

### Reference

## Installation

## Demo

## Github

## Wallet Compatibility

| Wallet (Android only) | Mobile Web (Local) |
| --------------------- | ------------------ |
| Seed Vault Wallet     | ✅                  |
| Solflare              | ✅                  |
| Phantom               | ✅                  |

## Browser Compatibility

| Platform                 | Mobile Web (Local) | Notes                                                 |
| ------------------------ | ------------------ | ----------------------------------------------------- |
| Android - Chrome         | ✅                  | Primary Android browser; also works with Chrome PWAs. |
| Android - Other Browsers | ❌                  | Firefox, Opera, Brave, etc. do not support MWA.       |
| iOS - All Browsers       | ❌                  | MWA is not available on any iOS browser.              |
