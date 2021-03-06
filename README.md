# go-telegram-bot

Simple Telegram bot go lang version example, long polling method used.

![](https://img.shields.io/badge/release%20version-1.0.1-blue.svg) ![](https://img.shields.io/dub/l/vibe-d.svg)

First read [official bot docs ](https://core.telegram.org/bots/api/)

### How to use

Add your token in ```teleApi``` struct in main func

```go
  var teleApi = &TeleAPI{
    apiUrl:  "https://api.telegram.org/bot",
    token:   "<YOUR TOKEN>",
    getMsg:  "/getUpdates",
    sendMsg: "/sendMessage",
    sendPhoto:  "/sendPhoto",
    offset:  0,  // initial offset
    timeout: 25, // any number, but I'm recommend you set 20-30 seconds
    limit:   1,  // get message one by one
  }
 ```

Handle incoming messages in ```SendMessage``` method in **gopherbot.go** file

```go
  switch strings.ToLower(text) {
  case "/start":
    send(t.sendMsg, `"text": "Hello, *` + name +
      `*. I'm *GopherBot*.\nLet's play ping-pong",` +
      `"parse_mode": "markdown"`)
    send(t.sendMsg, `"text": "ping"`)
  case "ping":
    send(t.sendMsg, `"text": "pong"`)
  case "pong":
    send(t.sendMsg, `"text": "ping"`)
  case "hi", "hello":
    send(t.sendMsg, `"text": "Hello"`)
  default:
    send(t.sendPhoto, `"photo": ` +
      `"AgADAgADqacxG2ILjA4QcjhJtLpIW8c6Sw0ABOCfmywocrQrnooBAAEC",` +
      `"caption": "WAT?"`)
  }
```

Then run in terminal

```
go run gopherbot.go
```

or build and run binaries

```
go build gopherbot.go
```
See how it works (Telegram should be installed) [http://telegram.me/gopherBot](http://telegram.me/gopherBot)
