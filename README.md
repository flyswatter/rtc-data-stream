# rtc-data-stream

convert a reliable [RTCDataChannel](http://dev.w3.org/2011/webrtc/editor/webrtc.html#rtcdatachannel) into a stream

use HTML5 [WebRTC](http://www.webrtc.org/) the node way -- with streams

## use

you can use [browserify](http://github.com/substack/node-browserify) to package this module for browser use.

```javascript
var rtcDataStream = require('rtc-data-stream')
var quickconnect = require('rtc-quickconnect')

quickconnect('http://rtc.io/switchboard', { room: 'rtc-data-stream-demo' })
  .createDataChannel('chat')
  .on('channel:opened:chat', function(peerId, channel) {
    var rtc = rtcDataStream(channel)
    rtc.pipe(somewhereAwesome)
  })
```

`rtc` is a stream and speaks stream events: `data`, `error` and `end`. that means you can pipe output to anything that accepts streams.

## demo
Open [this demo](http://requirebin.com/?gist=1ac2891d276ae07e46cd) in two windows to start a chat over rtc-data-stream

## hack
```
# install beefy
npm install -g beefy
# clone repo
git clone https://github.com/kumavis/rtc-data-stream
cd rtc-data-stream
# install dev dependencies
npm install
# start the example
npm start
# open another tab with the generated link
```

## credit
Based on [websocket-stream](https://github.com/maxogden/websocket-stream) by [max ogden](https://twitter.com/maxogden)

## license
BSD LICENSE
