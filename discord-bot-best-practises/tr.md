# Discord botları için en iyi uygulamalar

*Not: Bu yönergeler, genel sunucularda çalışan botlara yöneliktir. Botunuz özel olanlarla sınırlıysa, bu belge muhtemelen sizin için geçerli olmayacaktır veya değildir. Botunuzu [Discord Extreme Listesinde](https://discordextremelist.xyz/bots/submit) listelerken bunları karşılamanız **zorunludur**.*

## Komut Önekleri

1. **Komutlar açıkça çağrılmalı veya kullanılmalıdır**
Botlar normal sohbette etkinleştirilmemelidir. Bunun yerine, bir komut öneki kullanın veya yalnızca botunuz doğrudan @mentioned (@etiketlenmiş) olduğunda yanıt vermesini sağlayın.

2. **Benzersiz önekler kullanmaya özen gösterin**
`!`, `$` ve `.` gibi tek karakterli önekler, komutları etkinleştirmek için yaygın olarak kullanılır ve diğer botlarla çakışmalara yol açar.
Botunuz için bir önek kullanmayı seçerseniz, kelimeler (`baykuş`) veya benzersiz Unicode karakterler (`¨`) kullanmayı düşünün.
Ayrıca, bir kanaldan veya bir üyeden bahsetmek için kullanılabildiğinden, ön ek olarak `#` veya `@` kullanmaktan kaçınmalısınız.
İdeal olarak, botunuzun öneki sunucu bazında yapılandırılabilir olmalıdır, böylece sunucu sahipleri her botun kendi seçtikleri benzersiz önekine sahip olmasını sağlayabilir ve karmaşa oluşmasını engelleyebilirler.

3. **Açgözlü olmayın**
Başkalarıyla çarpışma riskini azaltmak için kendinizi az sayıda önekle sınırlayın.

4. **Bahsetmeleri aşırı kullanmayın**
Doğrudan bir komuta yanıt verirseniz, söz kullanmayın, bunlar bot yanıt döngülerine yol açabilir. Uzun süredir devam eden bir komut yürütülürse bahsetmeler iyi olacaktır, ancak özel mesajlar iyi bir alternatiftir.

5. **`/` önekini kullanmayın**
Botunuzun varsayılan öneki olarak `/` varsa, güncellenmiş Discord'un ui eğik çizgi komutlarına müdahale eder, yani sunucuda aynı ada sahip bir eğik çizgi komutu varsa, örneğin `/ping`, botunuzun ping komutu kullanılamaz hale gelebilir. Yedek önek olarak `/` kullanabilirsiniz, ancak buna yalnızca botunuz aynı ad ve işlevlere sahip eğik çizgi komutlarına sahipse izin verilir.

## Komutlar

1. **Bir `yardım` komutuna sahip olun**
Kolayca erişilebilen bir yardım komutu mutlak bir gerekliliktir, kullanıcılar bu komut sayesinde gerekli yardıma erişebilirler.

2. **`invalid command` (`geçersiz komut`) ile yanıt vermeyin**
Bir kullanıcı mevcut olmayan bir komut kullanıyorsa, sessizce başarısız olmasına izin verin.
"Invalid Command" (`Geçersiz Komut`) gibi bir şeyle yanıt vermeyin.
Komut doğruysa, ancak argümanlar yanlışsa, "geçersiz argümanlar" ile yanıt vermek sorun değil. Bir sunucuda bir önek paylaşan birden fazla bot varsa, bu çok rahatsız edici durumlara neden olabilir.

3. **Bahsetmeleri sterilize edin**
Komutlar `@roles`, `@everyone` veya `@here` ping atmak için kötüye kullanılamaz ve kullanılmamalıdır.
Bu, `allowed_mentions` kullanılarak halledilebilir. (`allowed_mentions` object - [referansı görüntüle](https://discord.com/developers/docs/resources/channel#allowed-mentions-object), [Türkçe allowed_mentions DEL yardımı](https://github.com/discordextremelist/help/blob/master/allowed_mentions/tr.md)).

## API ve davranışlar

1. **Discord'un API'sine saygılı olun**
Discord API'sini kötüye kullanan botlar, herkes için işleri mahveder.
Bot kodunuzda hız sınırlama ve geri çekilmeyi hesaba kattığınızdan emin olun ve API'yi kullanma konusunda akıllı olun.
Bir şeyleri uygulamanın doğru yolundan emin değilseniz yardım isteyin, yardım almak en doğru seçim olacaktır.

2. **Kendinizin ve diğer botların mesajlarını görmezden gelin**
Bu, sonsuz kendi kendine döngüleri ve olası güvenlik açıklarını önlemeye yardımcı olur. Her mesajın başında `\u200B` ve `\u180E` gibi sıfır genişlikte bir boşluk kullanmak, botunuzun diğer botların komutlarını tetiklemesini de engeller.

Discord API ayrıca bir kullanıcının bot olup olmadığını da söyler. (`bot` property on `User` objects - [referansı görüntüle](https://discordapp.com/developers/docs/resources/user#user-object)).

3. **NSFW özelliklerini NSFW kanallarına kilitli tutun**
Tüm NSFW komutları/özellikleri yalnızca (Discord) NSFW işaretli kanallarda çalışmalıdır.

4. **Kullanıcılara yardımcı olmak için bottan bahsetmeyi kullanın.**
Ön ek olarak bahsedilmesine izin vermek ("@MyBot yardım") veya yalnızca bir sözle ("@MyBot" veya "@MyBot, önekiniz nedir?") ile botun önekini bulmanın bir yolunu eklemek, sizin için yeni olan kullanıcılara yardımcı olacaktır. (Mesaj ne olursa olsun, kolayca bulunduğundan emin olun. Bunu yapmanın harika bir yolu, mesajı botunuzun özel durumuna eklemek olacaktır.)
Alternatif olarak, onu bulmak için kaba kuvvet kullanan noktalama işaretleridir; bu, 2 ve 3'ten sonraki botlar için zor olacaktır. Ayrıca, bahsetme, hepsinin en benzersiz önekidir.

## Hakkında

Bu belgeye bir ekleme veya değişiklik fikriniz varsa, lütfen bir pull request yapın.

Forked from [Andre601/discord-bot-best-practices](https://github.com/Andre601/discord-bot-best-practices).
