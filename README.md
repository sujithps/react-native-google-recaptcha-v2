
## react-native-google-recaptcha-v2
## Implement Google recaptcha v2 in React Native (both Android an iOS)


## Add it to your project

1. Insall package
- Using NPM
   `npm install react-native-google-recaptcha-v2` 
- Using Yarn
   `yarn add react-native-google-recaptcha-v2`
2. Import package
`import ConfirmGoogleCaptcha from 'react-native-google-recaptcha-v2';`


## Dependencies

1. [react-native-modal](https://github.com/react-native-community/react-native-modal)

2. [react-native-webview](https://github.com/react-native-community/react-native-webview)


## Usage

### Check demo in [Snack link](https://snack.expo.io/@xuho95/react-native-google-recaptcha-v2)


```javascript
import React from 'react';
import ConfirmGoogleCaptcha from 'react-native-google-recaptcha-v2';
const siteKey = 'you_site_key';
const baseUrl = 'base_url';
class App extends React.Component  {
    onMessage = event => {
         if (event && event.nativeEvent.data) {
            if (['cancel', 'error', 'expired'].includes(event.nativeEvent.data)) {
                this.captchaForm.hide();
                return;
            } else {
                console.log('Verified code from Google', event.nativeEvent.data);
                setTimeout(() => {
                    this.captchaForm.hide();
                    // do what ever you want here
                }, 1500);
            }
        }
    };
    render() {
        return (
            <View style={styles.container}>
                <ConfirmGoogleCaptcha
                    ref={_ref => this.captchaForm = _ref}
                    siteKey={siteKey}
                    baseUrl={baseUrl}
                    languageCode='en'
                    onMessage={this.onMessage}
                />
                <Button
                    onPress={() => {
                        this.captchaForm.show();
                    }}
                    title='Click'
                    style={{ width: 120, backgroundColor: 'darkviolet' }}
                    textColor='#fff'
                />
            </View>
        );
    }
}
```

### Note
You can `import GoogleReCaptcha from 'react-native-google-recaptcha-v2/GoogleReCaptcha';` to customize UI by yourself 


## DEMO

### iOS
![iOS](https://github.com/xuho/demo-images/blob/master/ios.gif?raw=true)

### Android
![Android](https://github.com/xuho/demo-images/blob/master/android.gif?raw=true)



## Props

- **`siteKey`** _(String)_ - The site key of the Google Recaptcha.
- **`baseUrl`** _(String)_ The url domain defined on your Google Recaptcha.
- **`onMessage`** _(Function)_ - The callback function  after received response, error of Google captcha or when user cancel
- **`languageCode`** _(String)_ - Language to be display of captcha form. Can be found at [this link](https://developers.google.com/recaptcha/docs/language)
- **`cancelButtonText`** _(String)_ - Title of cancel button.


## License
**MIT Licensed**

## Support me
<a href="https://www.buymeacoffee.com/xuho" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
