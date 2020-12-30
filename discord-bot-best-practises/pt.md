# Melhores práticas para Discord Bots


*NB: Estas diretrizes são destinadas a bots em execução em servidores públicos. Se o seu bot é restrito a servidores privados, este documento não lhe deve ser aplicado. É um **requisito** cumpri-los quando listar o seu bot [Discord Extreme List](https://discordextremelist.xyz/bots/submit).*

## Prefixos de Comandos

1. **Os comandos devem ser invocados explicitamente**  
Os bots não devem ser ativados em conversa normal. Pelo contrário, deve user um prefixo de comando ou só responder quando o seu bot é diretamente @mencionado.

2. **Use prefixos únicos**  
Prefixos de um único caractere tais como `!`, `$` e `.` são comuns para ativar comandos e tendem a sobrepor-se a outros bots.
Se optar por um prefixo para o seu bot, considere usar palavras (`coruja`) ou caracteres Unicode únicos (`¨`). 
Além disto, deve evitar usar `#` ou `@` como prefixos pois estes podem ser usados para mencionar um canal ou um membro.
Idealmente, o prefixo do seu bot deve ser configurável por servidor, de modo a que os donos dos servidores possam assegurar que cada bot tem o seu prefixo único à sua escolha.

3. **Não seja ganancioso**  
Restrita-se a um baixo número de prefixos para reduzir o risco de colisão com outros.

4. **Não abuse das menções**  
Se responder diretamente a um comando, não mencione, pois isto pode levar a ciclos de resposta de bot. As menções são adequadas a comados de longa duração, mas as mensages privadas são uma boa alternativa.

## Comandos

1. **Ter um comando `help` (de ajuda)**  
Um comando de ajuda facilmente acessível é um requisito absoluto.

2. **Não responda com "comando inválido"**  
Se um utilizador usar um comando que não existe então deixe falhar de forma silenciosa. 
Não tenha uma resposta do género "comando inválido"
Contudo, se o comando é correto mas os argumentos estão errados então pode responder com "argumentos inválidos". Se houver mais do que um bot num servidor que partilha um prefixo, então isto pode gerar uma utilização bastante desagradável.

3. **Higienizar menções**
Os comandos não devem possibilitar o abuso por mencionar `@cargos`, `@everyone` ou `@here`. 
Isto pode ser tratado ao usar `allowed_mentions`. (`allowed_mentions` objeto - [veja a referência](https://discord.com/developers/docs/resources/channel#allowed-mentions-object), [allowed_mentions DEL ajuda](https://github.com/discordextremelist/help/blob/master/allowed_mentions/pt.md)).
    
## API e comportamento

1. **Respeite a API do Discord**  
Os bots que abusam e usam impropriamente a API do Discord API estragam tudo a todos. 
Certifique-se do fator de rate-limiting e do backoff no código do seu bot, e seja inteligente em como usar a API. 
Certifique-se de pedir ajuda quando não tem a certeza da forma correta de implementar algo.

2. **Ignore tanto as mensagens do seu como de outros bots**  
Isto ajuda a prevenir ciclos infinitos e exploits de segurança. Usar um zero width space como `\u200B` e `\u180E` no início de cada mensagem também previne que o seu bot desencadeie comandos de outros bots. 
A API do Discord também lhe diz que se um utilizador é um bot (propriedade `bot` em objetos `User` - [veja a referência](https://discordapp.com/developers/docs/resources/user#user-object)).

3. **Mantenha características NSFW nos canais NSFW**  
Todos os comandos e características NSFW só devem funcionar em canais marcados (pelo Discord) como NSFW.

4. **Use a menção do bot para ajudar utilizadores.**  
Permitir uma menção como prefixo ("@MeuBot ajuda") ou adicionar uma forma de saber o prefixo do seu bot com apenas uma menção ("@MeuBot" ou "@MeuBot, qual é o teu prefixo?") irá ajudar os novos utilizadores de começar a usar o seu bot. (Certifique-se que, independente da mensagem, é fácilmente descoberta. Uma boa forma de alcançar isto é incluí-la na presença do seu bot.) 
A alternativa é usar força bruta e tentar todos os caracteres para encontrar o prefixo, isto que tornará difícil para bots que sigam as alíneas 2 e 3. Ainda assim, uma menção é o prefixo mais único de todos.

## Sobre

Se tem alguma ideia para alguma adição ou alteração a este documento, por favor faça um pull request.

Forked de [Andre601/discord-bot-best-practices](https://github.com/Andre601/discord-bot-best-practices).
