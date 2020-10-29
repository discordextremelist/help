# Allowed Mentions
Trying to sanitize mentions? Here are few examples what you should use.

*Note: Make sure you're looking at your library example and you have the required library version or higher installed otherwise it won't work.*

## Discord.py (requires v1.4.0 or higher)

There are multiple options: 
1) Add `, allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False)` after the output of your command. (Works for individual messages only).
2) Put it into your client. (If you do this, all messages your bot sends will ping nobody by default).

**╠ Example 1** If you have it subclassed [[src]](https://github.com/TheMoksej/Dredd/blob/76ff9608af1bd5a09a89f523996d57103a83b471/bot.py#L107):
```py
class Bot(commands.AutoShardedBot):
    def __init__(self, **kwargs):
        super().__init__(
            allowed_mentions = discord.AllowedMentions(roles=False, users=False, everyone=False),
        )
```

**╚ Example 2** If it's not subclassed [[src]](https://github.com/discordextremelist/bot/blob/915d203ca2b4ae4bbf9f55cb303c5dc5a4b17e8f/bot.py#L59):
```py
bot = commands.Bot(allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False))
```

## Discord.JS (requires v12.2.0 or higher)

There are multiple options:
1) Add `, {allowedMentions: {parse: []}}` after the output of your command. (Works for individual messages only).
2) Put it into the client. (If you do this, all messages your bot sends will ping nobody by default).

**╚ Example** [[src]](https://github.com/discordextremelist/website/blob/5394fcd179d5fc75e0ef9fbb9e674186a13f620a/src/Util/Services/discord.ts#L30)
```js
const client = new Discord.Client({
    allowedMentions: { parse: [] }
});
```

## Eris (requires 0.12.0 or higher)

There is currently only one known option. If this does not work please refer yourself to the [Eris documentation](https://abal.moe/Eris/docs/PrivateChannel#function-createMessage).

**╚ Example** Add this to your Eris options. [[src]](# "Franklin#8888 (425966117840748545)")
```js
{
  allowedMentions: {
    roles: false,
    everyone: false
  }
}
```
