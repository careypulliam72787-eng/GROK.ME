# Submit an Update

When you’re ready to publish an updated release of your dApp, follow these steps.

{% stepper %}
{% step %}
## Navigate to the Publisher Portal

Log into the [Solana dApp Publisher Portal](https://publish.solanamobile.com/) and find your published app in the sidebar.
{% endstep %}

{% step %}
## Update your app details

If needed, you can make changes to your app details (e.g Name, Descriptions, Preview Assets, etc) in the “Details” page.

{% hint style="info" %}
**NOTE:** These changes will only reflect in the dApp Store after a new release version is approved.
{% endhint %}

![](<../.gitbook/assets/update dapp details.png>)
{% endstep %}

{% step %}
## Submit an updated release version

Navigate to your app’s “Home” screen and press the “New Version” button.

### Submit an existing APK

If you only want to make a change to your app details and do not want to submit a new APK build, then select the **“use existing APK”** option.

### Submit an updated APK

If you want to submit a new APK, ensure:

* The APK is signed with the same Android signing key you used for your initial release.
* The `versionName` and `versionCode` value is properly incremented between each update.
* The “What’s new” section is filled out. This section will be displayed to users in your dApp Store listing page.

After you’ve completed the upload, press “Submit” and you’ll be prompted to sign messages and transactions for uploading to Arweave and minting your Release NFT.

![](<../.gitbook/assets/dapp update upload.png>)

Congratulations on submitting an app update! 🎉
{% endstep %}
{% endstepper %}

## After submission

Once submitted, the new release automatically enters the app review queue and will immediately go live once approved.

### App Review

* Review results are sent to your developer email from `publishersupport@dappstore.solanamobile.com` within 3-5 business days.
* Apps are reviewed in the order they are submitted.
* If you haven’t received a response after 5 business days, submit an **App Review Inquiry** in the `#dev-answers` channel on [Discord](http://discord.gg/solanamobile).

### Get Support

For questions about publishing, app review, or launching on the dApp Store, see the [dApp Store Support](get-support.md) page. Join the [Solana Mobile Discord](http://discord.gg/solanamobile), get the **Developer** role, and use the `#dev-answers` channel for assistance.
