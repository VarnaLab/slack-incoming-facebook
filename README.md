
# Install

```bash
npm install -g slack-webhook-facebook
```

# CLI

```bash
slack-webhook-facebook \
  --env development|staging|production \
  --config path/to/config.json \
  --db path/to/db.json
```

# config.json

```js
{
  "development": {
    "facebook": {
      "id": "[Group ID]",
      "token": "[OAuth Access Token]"
    },
    "slack": {
      "hook": "[Hook URL]", // or ["[Hook URL 1]", "[Hook URL N]"]
      "username": "[Bot Name]",
      "icon_url": "[Bot Avatar]",
      "channel": "[Target Channel or User]"
    }
  }
}
```

# db.json

```js
{
  "development": {
    "timestamp": 1486676489575
  }
}
```

# Crontab

```bash
# Check on every 15 min:
*/15 * * * * node slack-webhook-facebook [params] >> facebook.log
```

# API

```js
var hook = require('slack-webhook-facebook')
hook.init({
  env: 'development',
  config: require('config.json'),
  db: require('db.json')
})
// Check on every 15 min:
setTimeout(() => hook.check, 1000 * 60 * 15)
```
