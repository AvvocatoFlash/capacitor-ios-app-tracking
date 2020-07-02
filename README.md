
# [Capacitor-iOS-App-Tracking](https://github.com/migtam628/capacitor-ios-app-tracking) 

Capacitor-iOS-App-Tracking is a native AppTrackingTransparency implementation for iOS 14. Now you can use this package as a [Ionic Capacitor](https://capacitor.ionicframework.com) Plugin in your App.

<!-- Badges -->
<a href="https://npmjs.com/package/capacitor-ios-app-tracking">
  <img src="https://badgen.net/npm/v/capacitor-ios-app-tracking">
</a>
<a href="https://npmjs.com/package/@capacitor-community/apple-sign-in">
  <img src="https://badgen.net/npm/dt/capacitor-ios-app-tracking">
</a>
<a href="https://npmjs.com/package/@capacitor-community/apple-sign-in">
  <img src="https://badgen.net/npm/license/capacitor-ios-app-tracking">
</a>

## Release Note:

### v0.0.7
- Implemented iOS 14 AppTrackingTransparency.

## Supported Platform:
- [x] iOS
- [ ] Android


<!--
## Other Plugins:
| Plugins                                             | Android | iOS | Electron | PWA |
| :-------------------------------------------------- | :------ | :-- | :------- | :-- |
| [AdMob Native](https://github.com/migtam628/capacitor-admob-native) | ✅      |✅  | ❌       | ❌  |
-->
## Supported methods
| Name              |
| :---------------- |
| getTrackingStatus |
| requestPermission |  

## Installation

Use **Capacitor-iOS-App-Tracking** plugins in your app.

```console
 npm install --save capacitor-ios-app-tracking
```

## iOS

### Update **Info.plist**

Open your **App/App/Info.plist** file and add this `plist value` line at the right spot (and replace the value with the message for the user!):

````xml

<key>NSUserTrackingUsageDescription</key>
<!-- replace this value with your message-->
<string>Message to Users.</string>

````

## Usage

```typescript
import React, { useEffect } from "react"
import { Plugins } from "@capacitor/core";

const { IOSAppTracking } = Plugins;

const App: React.FC = () => {
  const [ response, setResponse ] = useState<Response>()

  useEffect(() => {
    IOSAppTracking.getTrackingStatus().then((res: Response ) => setResponse(res))
  }, [])
  
  useEffect(() => {
    if(response.status === 'unrequested') {
      IOSAppTracking.requestPermission().then((status: Status) => console.log(status))
    }
  }, [response])
 
 ...
}

interface Response {
  value: string;
  status: Status;
}

type Status = 'authorized' | 'denied' | 'unrequested' | 'restricted' 


```


## Contributing

- 🌟 Star this repository
- 📋 Open issue for feature requests


## Roadmap

- [Capacitor Plugins](https://capacitor.ionicframework.com/docs/plugins/)

- [IOS](https://capacitor.ionicframework.com/docs/plugins/ios/)


## License

Capacitor-iOS-App-Tracking is MIT licensed.

