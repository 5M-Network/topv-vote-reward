# TopV Votes Reward

A FiveM resource that rewards players for voting on [TopV.gg](https://topv.gg/).

## Configuration

### 1. Get your server URL

Your server must be reachable via **HTTPS** (not HTTP). The callback URL will be:

```
https://<your-server-ip-or-domain>:<port>/api/topv-vote
```

### 2. Set up the callback on TopV.gg

1. Go to [https://topv.gg/](https://topv.gg/)
2. Navigate to **Dashboard** → **Your server name** → **In-Game integration**
3. Under **Vote callback (top-serveurs style)**, enter your callback URL (must use `https://`)
4. Click **Generate** or enter a **Secret** of your choice
5. Copy the secret

### 3. Edit `config.json`

Open `config.json` in the resource folder and replace `"your TopV integration secret"` with the secret you created:

```json
{
  "secret": "the-secret-you-generated",
  "discordWebhook": "https://discord.com/api/webhooks/...",
  ...
}
```

> **⚠️ Never share your secret.** Anyone with it can forge vote callbacks.

### 4. Start the resource

Add `ensure topv-votes-reward` to your `server.cfg` and restart your server.

## Commands

| Command | Description |
|---------|-------------|
| `/vote-claim` | Claim your pending vote rewards |
| `/vote-count` | Check how many pending votes you have |

## Config Options

| Field | Description |
|-------|-------------|
| `secret` | Your TopV.gg integration secret |
| `discordWebhook` | Discord webhook URL for vote notifications (leave empty to disable) |
| `discordBotName` | Name shown for the Discord webhook |
| `discordBotAvatar` | Avatar URL for the Discord webhook |
| `votesPerReward` | How many votes are needed for one reward claim |
| `rewards` | List of rewards (supports `money`, `bank`, `black_money`, `item`) |

## Dependencies

- [oxmysql](https://github.com/overextended/oxmysql)
- [ox_lib](https://github.com/overextended/ox_lib)
