# DeviceCheck Sample
DeviceCheck is a new iOS 11 API that gives you access to two bits of data per-device, per-developer that your associated server can use in its business logic. Here's a fully working sample.

# Uses
- webservice request on server comes from apple devices.
- App device token using device check is ephemeral, but that token is useful to identify the device uniqueness such as per device per app one offer scenario. If device formatted, keychain wipe or any hack won't effect on this case. Safe to check per device identification.

# Getting started
All you have to do in the iOS project is change the host to your NodeJS server's IP. You can do this in ViewController.swift:
````
let host = "http://10.1.1.1:3000" // Change to your NodeJS server IP:port
````


# NodeJS server
Getting the NodeJS server to work is a tiny bit more involved.
The NodeJS server is dependent on a few NodeJS libraries namely: `'jsonwebtoken'`, `'uuid'`, `'express'`, `'body-parser'`. To install these dependencies you can use `npm install`, this will install the dependencies from the package.json.

In sampleServer.js you'll find a few configurable variables. Fill in your own IDs and key.

````
/****************** Set your values ******************/
var keyFileName = 'AuthKey_###.p8'; // Download from https://developer.apple.com/account/ios/authkey/
var keyId = "###"; // Can be found at: https://developer.apple.com/account/ios/authkey/
var teamId = "###"; // Can be found at: https://developer.apple.com/account/#/membership/

var port = 3000;

// Change this to true when you're app is on the App Store
var production = false;
/****************** End set your values ******************/
````

After you have configured your NodeJS server, you can run it with.

````
node sampleServer.js
````

After that your app will be able to talk to the NodeJS server.

# Apple Docs
iOS docs:
<https://developer.apple.com/documentation/devicecheck>

Server side docs:
<https://developer.apple.com/documentation/devicecheck/accessing_and_modifying_the_per_device_data>

WWDC 2017 - Session 702 - Privacy and Your Apps:
<https://developer.apple.com/videos/play/wwdc2017/702/?time=1444>


Updates: https://github.com/marinosoftware/DeviceCheckSample + Apple device check `validate_device_token` api added
