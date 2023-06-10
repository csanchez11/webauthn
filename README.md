# WebAuthn / FIDO2 API Codelab
This folder contains the source code for the WebAuthn / FIDO2 API codelab. It gives an introduction into implementing FIDO2 API,


[https://codelabs.developers.google.com/codelabs/webauthn-reauth/](https://codelabs.developers.google.com/codelabs/webauthn-reauth/)
[https://codelabs.developers.google.com/codelabs/fido2-for-android/](https://codelabs.developers.google.com/codelabs/fido2-for-android/)


# Summary

The Web Authentication API, also known as WebAuthn, lets you create and use origin-scoped, public-key credentials to authenticate users.

The API supports the use of BLE, NFC, and USB-roaming U2F or FIDO2
authenticators—also known as security keys—as well as a platform
authenticator, which lets users authenticate with their fingerprints or
screen locks.

For more information I found this [WebAuthn guide](https://webauthn.guide/) to be really helpful in explaining what is happening behind the scene.

## Create New Credential
- The Client calls FIDO Server to get Challenge Token and WebAuthn Options object
- Client calls navigator.credentials.create() with public key Options object from above 
  - `{ publicKey: options }`
  - This prompts the authenticator device to create a public/private key pair
  - Private key hidden behind authenticator device's authentication (ex. TouchID)
- Client sends public key to FIDO server to be registered with user as an accepted credential


## Authenticate Using Credential
- Client calls FIDO Server with credential ID
  - Server returns challnege token inside WebAuthn options object
- Client calls navigator.credentials.get() with options object
  - This will prompt user to authenticate with device (ex. TouchID) to retrieve the private key
- Client Calls FIDO Server with the private key to authenticate the user session
- FIDO Server authenticates and generates session

---

    License
    Copyright 2019 Google, Inc.

    Licensed to the Apache Software Foundation (ASF) under one or more contributor
    license agreements. See the NOTICE file distributed with this work for
    additional information regarding copyright ownership. The ASF licenses this
    file to you under the Apache License, Version 2.0 (the "License"); you may not
    use this file except in compliance with the License. You may obtain a copy of
    the License at

    [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
    WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
    License for the specific language governing permissions and limitations under
    the License.
