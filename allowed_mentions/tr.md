# İzin verilen Bahsetmeler (Allowed Mentions)
Bahsetmeleri temizlemeye mi çalışıyorsunuz? İşte kullanmanız gereken birkaç örnek.

*Not: Kitaplık örneğinize baktığınızdan ve gerekli kitaplık sürümünün veya daha üstünün kurulu olduğundan emin olun, aksi takdirde stabil çalışmaz.*

## Discord.py (v1.4.0 veya daha günceli)

Birden çok seçenek var:
1) Komutunuzun çıktısından sonra `, allow_mentions=discord.AllowedMentions(roles=False, users=False, Everyone=False)` ekleyin. (Yalnızca bireysel mesajlar için çalışır).
2) Client'inize koyun. (Bunu yaparsanız, botunuzun gönderdiği tüm mesajlar varsayılan olarak kimseye ping atmaz).

**╠ Örnek 1** Alt sınıfa sahipseniz [[src]](https://github.com/TheMoksej/Dredd/blob/76ff9608af1bd5a09a89f523996d57103a83b471/bot.py#L107):
```py
class Bot(commands.AutoShardedBot):
    def __init__(self, **kwargs):
        super().__init__(
            allowed_mentions = discord.AllowedMentions(roles=False, users=False, everyone=False),
        )
```

**╚ Örnek 2** Alt sınıflı değilse [[src]](https://github.com/discordextremelist/bot/blob/915d203ca2b4ae4bbf9f55cb303c5dc5a4b17e8f/bot.py#L59):
```py
bot = commands.Bot(allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False))
```

## Discord.JS (v12.2.0 veya daha günceli)

Birden çok seçenek var:
1) Komutunuzun çıktısından sonra `, {allowMentions: {parse: []}}` ekleyin. (Yalnızca bireysel mesajlar için çalışır).
2) Client'inize koyun. (Bunu yaparsanız, botunuzun gönderdiği tüm mesajlar varsayılan olarak kimseye ping atmaz).

**╚ Örnek** [[src]](https://github.com/discordextremelist/website/blob/5394fcd179d5fc75e0ef9fbb9e674186a13f620a/src/Util/Services/discord.ts#L30)
```js
const client = new Discord.Client({
    allowedMentions: { parse: [] }
});
```

## Eris (v0.12.0 veya daha günceli)

Şu anda bilinen tek bir seçenek var. Bu işe yaramazsa lütfen bu [Eris Dökümantasyonlarına](https://abal.moe/Eris/docs/PrivateChannel#function-createMessage) bakın.

**╚ Örnek** Bunu Eris ayarlarına ekleyin. [[src]](# "Franklin#8888 (425966117840748545)")
```js
{
  allowedMentions: {
    roles: false,
    everyone: false
  }
}
```
