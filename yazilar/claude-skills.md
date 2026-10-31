# Bir Kez Anlat, Hep Bilsin

**Claude'un "skill" denen yetenek dosyaları ne işe yarar, nasıl çalışır, nereye konur — Anthropic'in kendi anlatımıyla, bizim kurulumdan örneklerle.**

---

*Kaynak: "What are skills?" · Claude (Anthropic'in resmî YouTube kanalı) · 2 dk 54 sn · 27 Şubat 2026. Video kısa; bu yazı onun beş bölümünü sırasıyla anlatıyor ve her bölüme bizim kendi kurulumumuzdan bir karşılık ekliyor.*

## Sorun: aynı şeyi her seferinde baştan anlatmak

[0:00 · videoda dinle](https://www.youtube.com/watch?v=bjdBVZa66oU&t=0s)

Video bir tanıdık durumla açılıyor. Ekibinin kod yazma kurallarını Claude'a her seferinde yeniden anlatıyorsun. Her kod incelemesinde geri bildirimi nasıl istediğini tekrar tarif ediyorsun. Her commit mesajında tercih ettiğin biçimi yeniden hatırlatıyorsun.

Anthropic'in cevabı tek cümle: **skill, Claude'a bir işin nasıl yapıldığını bir kez öğreten bir markdown dosyasıdır; Claude o bilgiyi, ne zaman gerekirse kendiliğinden uygular.**

Bunu bizim dünyamıza çevirelim. Etsy'de her yeni ürün için Claude'a "başlık 140 karakteri geçmesin, ilk kelimeler aranan terim olsun, 13 etiketin hepsini kullan" diyorsan, bu bir skill adayıdır. Kuzzat Altay'ın benzetmesiyle: garsona her sabah menüyü elle yazmak yerine bir kez basıp masaya koymak.

## Nasıl çalışır: açıklama kapıyı açar

[0:32 · videoda dinle](https://www.youtube.com/watch?v=bjdBVZa66oU&t=32s)

Teknik tanım şu: skill'ler, ajanın bulup kullanabileceği **talimat, betik ve kaynak klasörleridir**. Claude Code'da bu klasörün kalbi `SKILL.md` dosyasıdır.

Videonun en önemli cümlesi burada geçiyor: **Claude bir skill'i kullanıp kullanmayacağına açıklamaya (description) bakarak karar verir.** Sen "şu kod değişikliğini incele" dediğinde, Claude isteğini elindeki bütün skill açıklamalarıyla karşılaştırır ve eşleşenleri devreye sokar.

Bunun pratik sonucu büyük: talimatların kusursuz olabilir, ama açıklama kötüyse skill hiç açılmaz. Kuzzat Altay'ın kitabındaki "hata yardımcısı" örneği tam olarak bu: açıklama bir **konu** adlandırıyorsa eşleşme olmaz; bir **durumu** tarif ediyorsa olur.

**Bizde:** Kurduğumuz `video-yaziya` skill'inin açıklaması bu yüzden "video araçları" diye değil, şöyle başlıyor: *"Kullanıcı bir video linki attığında, 'bunu yazıya dök' dediğinde…"* Bu yazıyı da o skill üretti; sen "evet yap" dediğinde açıklama isteğinle eşleşti.

## Nereye konur: kişisel ve proje skill'leri

[1:05 · videoda dinle](https://www.youtube.com/watch?v=bjdBVZa66oU&t=65s)

Skill'lerin iki yeri var, ayrım "kim kullanacak" sorusuna göre:

**Kişisel skill'ler** ana klasördeki `~/.claude/skills` içinde durur ve seninle birlikte bütün projelere gelir. Bunlar senin tercihlerin: commit mesajı üslubun, doküman biçimin, kodun sana nasıl açıklanmasını istediğin.

**Proje skill'leri** projenin kök klasöründeki `.claude/skills` içinde durur. Projeyi indiren herkes onları otomatik alır. Ekip standartları buraya gider: markanın kuralları, sitede kullanılan fontlar ve renkler.

**Bizde:** `video-yaziya` kişisel skill olarak kuruldu, çünkü hangi projede olursan ol işine yarıyor. Ama Etsy mağazasının marka kuralları — renkler, ürün fotoğrafı dili, açıklama üslubu — bir gün proje skill'i olmalı. O zaman mağaza işini yapan diğer ajan da aynı kurallarla çalışır.

## Diğer ayarlardan farkı: kendiliğinden ve göreve özel

[1:43 · videoda dinle](https://www.youtube.com/watch?v=bjdBVZa66oU&t=103s)

Claude Code'un davranışını değiştirmenin birkaç yolu var ve video bunları birbirinden ayırıyor:

**CLAUDE.md** her konuşmaya yüklenir. "Her zaman şunu yap" denen kurallar oraya gider. Videodaki örnek: TypeScript'in sıkı modunu her zaman kullanmak.

**Skill** ise ihtiyaç anında yüklenir — isteğin onun açıklamasıyla eşleştiğinde. Başta yalnızca adı ve açıklaması yüklenir, bu yüzden bağlam penceresini (context window) doldurmaz. Videonun örneği: hata ayıklarken kod inceleme kontrol listenin bağlamda durmasına gerek yok; ancak inceleme istediğinde yüklenir.

**Eğik çizgi komutları** (slash commands) senin yazmanı gerektirir. Skill'ler gerektirmez; Claude durumu tanıyınca kendisi uygular.

**Bizde:** Bunu ölçtük. Kurulumumuzda 1.167 skill var ama başta yüklenen yalnızca adları — yaklaşık 7.100 token. Açıklamaların tamamı yüklenseydi bu 75.000 token olurdu. "Sadece ad ve açıklama yüklenir" ilkesi bütçede bu kadar fark yaratıyor. Bizim global CLAUDE.md'miz de bu yüzden kısa tutuluyor: her konuşmaya giren dosya ne kadar uzunsa, her mesaj o kadar pahalı.

## Ne zaman skill yazmalı

[2:27 · videoda dinle](https://www.youtube.com/watch?v=bjdBVZa66oU&t=147s)

Video, skill'in en iyi işlediği alanı şöyle tarif ediyor: **belirli görevlere uygulanan uzmanlık bilgisi.** Ekibin izlediği kod inceleme standartları, tercih ettiğin commit biçimi, kurumunun marka kuralları.

Ve kapanış ölçütü, bütün videonun özeti: **aynı şeyi Claude'a tekrar tekrar anlattığını fark ediyorsan, orada yazılmayı bekleyen bir skill var.**

---

## Bu kısım benim yorumum

Video kısa ve kasıtlı olarak sade. İki şeyi söylemiyor ama bilmen işine yarar:

**Skill'in içine betik koyabilirsin.** Video "talimat, betik ve kaynak klasörleri" deyip geçiyor. Oysa en güçlü skill'ler düz talimatın yanında her seferinde aynı işi aynı şekilde yapan küçük bir program taşır. `video-yaziya` skill'inin içinde iki tane var: konuşmayı yazıya çeviren `cozumle.py` ve metni bölümlere ayırıp her bölüme video linki koyan `bolumle.py`. Kuzzat Altay bunu James Bond'un saati diye anlatıyor: görevde ihtiyaç olunca kullanılan, her seferinde aynı çalışan alet.

**En iyi skill, iyi geçmiş bir oturumdan çıkar.** Bir işi Claude'la yirmi düzeltmeyle mükemmel bitirdiysen, o konuşmayı sakla ve yeni bir oturumda ondan skill çıkarttır. O yirmi düzeltme, skill'in içermesi gereken şeyin ta kendisidir.

**İlk skill'in için öneri:** Etsy ürün listeleme. Başlık kuralları, etiket stratejisi, açıklama yapısı, fotoğraf sırası. Her yeni üründe aynı şeyleri anlatıyorsan, yazılmayı bekleyen skill bu.

---

*Kaynak: [What are skills? — Claude, YouTube](https://www.youtube.com/watch?v=bjdBVZa66oU). Videonun otomatik altyazısından ve konuşmacının kendi bölüm başlıklarından yazıldı; çeviri değil, Türkçe anlatım. Otomatik altyazıdaki "claw.md", doğrusu olan CLAUDE.md olarak düzeltildi.*
