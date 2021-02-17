# Doctor Feeder

A watcher for news by Arknights.

## Installation

### Retrieve via Go command

```bash
$ go get -u github.com/hguandl/dr-feeder
```

### Build from source

```bash
$ git clone https://github.com/hguandl/dr-feeder.git
$ cd dr-feeder
$ go build
$ go install
```

## Usage

```bash
$ dr-feeder -h
Usage of dr-feeder:
  -c string
    	Configuration file (default "config.yaml")
```

## Example Configuation File

```yaml
### Currently the version is fixed to 1.0
version: 1.0

notifiers:
### Custom API server
# Send an HTTP POST form to <api_url>,
# which contains "title", "body" and "url".
##
- type: custom
  api_url: "http://localhost:8080/"

### Telegram bot
# Authencate a telegram bot with <api_key>
# to send messages to <chats>.
##
- type: tgbot
  api_key: "123456:foobar"
  chats:
    - "114514"
    - "-1919810"

### Work Wechat app
# See https://hguandl.com/posts/weibo-watcher-deploy/
##
- type: workwx
  corpid: "wx20190501"
  agentid: 1000002
  corpsecret: "rhodesisland"
  touser: "@all"

### iOS Bark
# Official API server: https://api.day.app
##
- type: bark
  tokens:
    - "qwertyuiop"
    - "asdfghjkl"

### IFTTT Webhook
# See https://maker.ifttt.com/use/demo-page
# (use your API key to replace "demo-page" above)
##
- type: ifttt
  webhooks:
    - event: "call"
      api_key: "amiya"
    - event: "sleep"
      api_key: "doctor"
```
