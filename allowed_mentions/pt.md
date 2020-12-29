# Menções Permitidas
Tentando higienizar menções? Aqui estão alguns exemplos do que usar.

*Nota: Tenha a certeza que está a ver o exemplo da sua biblioteca e que tem a versão necessária ou superior instalada, que de outra forma não funcionará.*

## Discord.py (requer v1.4.0 ou superior)

Existem várias opções: 
1) Adicionar `, allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False)` após o output do seu comando. (Apenas funciona para mensagens individuais).
2) Colocar no cliente. (Se fizer isto, todas as mensagens que o seu bot envia não irá mencionar alguém por defeito).

**╠ Exemplo 1** Se o tiver em subclasses [[fonte]](https://github.com/TheMoksej/Dredd/blob/76ff9608af1bd5a09a89f523996d57103a83b471/bot.py#L107):
```py
class Bot(commands.AutoShardedBot):
    def __init__(self, **kwargs):
        super().__init__(
            allowed_mentions = discord.AllowedMentions(roles=False, users=False, everyone=False),
        )
```

**╚ Exemplo 2** Se não estiver em subclasses [[fonte]](https://github.com/discordextremelist/bot/blob/915d203ca2b4ae4bbf9f55cb303c5dc5a4b17e8f/bot.py#L59):
```py
bot = commands.Bot(allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False))
```

## Discord.JS (requer v12.2.0 ou superior)

Existem várias opções:
1) Adicionar `, {allowedMentions: {parse: []}}` após o output do seu comando. (Apenas funciona para mensagens individuais).
2) Colocar no cliente. (Se fizer isto, todas as mensagens que o seu bot envia não irá mencionar alguém por defeito).

**╚ Exemplo** [[fonte]](https://github.com/discordextremelist/website/blob/5394fcd179d5fc75e0ef9fbb9e674186a13f620a/src/Util/Services/discord.ts#L30)
```js
const client = new Discord.Client({
    allowedMentions: { parse: [] }
});
```

## Eris (requer 0.12.0 ou superior)

Esta é a única opção conhecida. Se isto não funcionar por favor refira-se à [documentação da Eris](https://abal.moe/Eris/docs/PrivateChannel#function-createMessage).

**╚ Exemplo** Adicione isto às opções do seu Eris. [[fonte]](# "Franklin#8888 (425966117840748545)")
```js
{
  allowedMentions: {
    roles: false,
    everyone: false
  }
}
```
