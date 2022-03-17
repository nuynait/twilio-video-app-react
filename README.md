# What's This?

This repository is forked from twilio/twilio-video-app-react. The purpose to fork the repository is to reproduce [this issue](https://github.com/twilio/twilio-video.js/issues/1725). 

## What have I changed?

The only thing I have changed is to change the `group` type into `peer-to-peer`. You can peek the last commit for changes. 

## How to Reproduce?

1. Clone this repository

```

git@github.com:nuynait/twilio-video-app-react.git

```

2. Install dependencies

```
npm install
```

3. Install `ngrok`. I use that to test on local network with two different devices.

4. Config `ngrok` like this in `~/.ngrok2/ngrok.yml`.

```
authtoken: <YOUR AUTH TOKEN>
tunnels:
  first:
    addr: 8081
    proto: http
  second:
    addr: 3000
    proto: http
```

5. Build and start

```
npm run build

npm start
```

6. Run `ngrok`

```
ngrok start -all
```

7. Have two device visit the `ngrok` redirected url which looks like `https://abcd-123-123-123-12.ngrok.io`. 

8. Join the two devices as different user into the same room. 

9. Disconnect one of the device's network. 

### Expected:

Only one of the device into reconnecting state and the other device will remain connected in the room. 

### Actual:

Both devices gets into the reconnecting state. Both device is showing a snack bar of reconnecting. After a while, both device gets an error code: 53405 (Media connection failed or Media activity ceased)

## Screencast

Here is a video screencast. [Click here to download](https://share.tshan.me/7g1P). This link will be expired after 2022-03-25.
