# MCP: Yapay Zekâya Araç Vermenin Standart Yolu

**Model Context Protocol nedir, neden bir anda sektör standardı oldu, hazır bir MCP sunucusu nasıl kullanılır ve kendi sunucunu nasıl yaptırırsın.**

---

*Kaynak: "you need to learn MCP RIGHT NOW!!" · NetworkChuck · 38 dk 40 sn · 12 Eylül 2025 · 1,8 milyon izlenme. **Video Docker sponsorluğunda**; anlatımın büyük kısmı Docker Desktop'ın MCP araçları üzerinden ilerliyor. MCP'nin kendisi Docker'a bağlı değil.*

## Sorun: dil modelleri uygulamalarla nasıl konuşacak

[0:40 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=40s)

Bir dil modelini işe yarar kılmak için ona araç vermek gerekiyor: görev yöneticin, notların, e-postan. NetworkChuck sorunu adım adım açıyor.

İnsanlar uygulamaları ekranlar üzerinden kullanır; karmaşık kodu arayüz gizler. Ama dil modelleri arayüz sevmez; onların dili metin. "O zaman koda erişim verelim" — olmaz, uygulamalar kodlarını vermez. "API'ler var ya" — evet, API tam da bir programın başka bir programın araçlarını kullanması için var. Örneğin ClickUp, bir programın senin adına görev oluşturmasına izin veren bir API sunuyor.

Ama burada da iki engel çıkıyor. API'yi kullanmak kod çalıştırmayı gerektirir ve model çoğu zaman buna erişemez. Erişse bile her uygulamanın API belgesi yığın gibi; her etkileşimi tek tek kodlayıp modele nasıl yapacağını anlatman gerekir. İnsanlar bunu yapıyor ve çalışıyor, ama zahmetli ve standart bir yolu yok.

## Çözüm: MCP

[2:40 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=160s)

**MCP — Model Context Protocol** — dil modellerine araç vermenin standart yolu. NetworkChuck'ın benzetmesiyle, USB-C'nin kablo karmaşasını çözmesi gibi. Anthropic geliştirdi ve kısa sürede sektör standardı oldu.

Mantık şu: modelle API arasına bir **MCP sunucusu** giriyor. API ile konuşmak için normalde yazman gereken bütün kod bu sunucunun içinde hazır. Modele yalnızca "şu MCP sunucusuna bağlan" diyorsun. Sunucu "görev oluştur", "görevleri getir" gibi araçları sade bir dille sunuyor; model API'yi, kodu, kimlik doğrulamayı bilmek zorunda kalmadan istediği aracı çağırıyor. Konuşmacının deyişiyle, modeller için bir arayüz yaratmış oluyoruz: tek yapmaları gereken düğmeye basmak.

Asıl güç standart olmasında: modelin MCP'ye bağlanabiliyorsa — artık çoğu bağlanabiliyor — uygulamalarını MCP sunucusuyla sunan herkese bağlanabilirsin.

## İlk MCP sunucusunu çalıştırmak

[4:06 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=246s)

Gereken iki şey var: Docker Desktop ve MCP kullanabilen bir yapay zekâ uygulaması. Docker Desktop'ın yeni **MCP Toolkit**'i, hazır MCP sunucularından oluşan bir katalog sunuyor. NetworkChuck katalogdan Obsidian'ın (yerel çalışan, açık kaynak bir not uygulaması) MCP sunucusunu ekliyor, Obsidian'dan aldığı API anahtarını yapıştırıyor ve bitti. Sunucu 12 araç sunuyor, her biri sade bir dille tarif edilmiş: "kasadaki bir dosyaya içerik ekle", "basit arama yap".

## Üç farklı istemcide deneme

[7:32 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=452s)

**Claude Desktop:** Docker'da tek tıkla bağlanıyor. "Obsidian'ıma French press kahve yapmanın en iyi yolunu anlatan bir not oluştur" diyor; Claude bir aracı olduğunu fark ediyor, kullanmak için **izin istiyor** (çünkü normal sınırlarının dışına çıkıyor), not oluşuyor. Arama da aynı şekilde çalışıyor. Konuşmacının vurguladığı nokta: Claude kimlik doğrulamayı, kodu, API'yi hiç bilmiyor; yalnızca aracı çağırabileceğini biliyor.

Ardından katalogdan birkaç sunucu daha ekliyor: DuckDuckGo araması, web sayfası içeriği çeken Fetch, Airbnb araması, YouTube transkriptleri.

[10:12 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=612s)

**LM Studio (yerel modeller):** Aynı araçlar bilgisayarda çalışan modellere de bağlanıyor. Sonuç öğretici: Gemma 3 12B görevi yarım bırakıyor, düşünebilen DeepSeek tamamlıyor; aynı iş Claude'da çok daha hızlı gidiyor. Araç bağlamak kolay; aracı akıllıca kullanmak modelin kalitesine bağlı.

[11:48 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=708s)

**Cursor:** Bir YouTube videosunun transkriptini çekip özetleyip Obsidian'a not olarak ekliyor.

Arka planda olan şey basit: her uygulamanın bir MCP yapılandırma dosyası var ve Docker yalnızca o dosyayı güncelliyor.

## Kendi MCP sunucunu yaptırmak

[12:31 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=751s)

Videonun en değerli bölümü bu. Aradığın işi yapan bir MCP sunucusu yoksa, kendin yaptırabilirsin. NetworkChuck'ın sırrı uzun bir prompt: bir yapay zekânın MCP sunucusu kurmak için ihtiyaç duyacağı her şeyi içeriyor; sen sadece ne istediğini tarif ediyorsun. (Prompt ve örnekler konuşmacının GitHub sayfasında.)

İlk deneme bilerek basit: zar atan bir sunucu. Claude Opus 4.1'e veriyor; çıkan beş dosya — Docker dosyası, gereksinimler, sunucunun Python kodu, okuma notu ve CLAUDE.md — adım adım kuruluyor. Docker imajı derleniyor, kendi kataloğuna ve kayıt dosyasına ekleniyor, Claude'un yapılandırması güncelleniyor. Claude açılınca "iki tane altı yüzlü zar at" diyor, çalışıyor.

## Daha karmaşık bir sunucu: zaman takibi

[19:05 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=1145s)

Gerçek bir ihtiyaç: kullandığı zaman takip uygulaması Toggl'ın iyi bir API'si var ama MCP sunucusu yok. Prompt'a üç şey istediğini yazıyor — sayaç başlat, durdur, mevcut sayaçları göster — ve API belgesinin linkini ekliyor. Prompt, cevaplanmamış soru varsa sormaya da ayarlı.

Burada iki önemli ders veriyor. Birincisi: yapay zekâyla çalışırken her şey **bağlam**; iyi bağlam verirsen sonuç iyi olur. İkincisi: **API anahtarını koda yazma.** Docker'ın gizli bilgi yöneticisine (`docker mcp secret set`) koyuyor; anahtar koddan ayrı, güvenli bir yerde duruyor. Sonuç: "şu an çalışan bir sayacım var mı?" diye soruyor, hangi aracı kullanacağını söylemeden; Claude buluyor, durduruyor, yeniden başlatıyor.

## Kali Linux sunucusu

[23:19 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=1399s)

Üçüncü örnek bir güvenlik testi sunucusu: Kali Linux konteyneri içinde ağ taraması, web uygulaması taraması gibi araçlar. Test hedefi kasıtlı olarak güvensiz yapılmış bir alıştırma uygulaması (DVWA).

İlginç an şu: Claude sunucuyu yazarken kendiliğinden bir **beyaz liste** koyuyor — yalnızca izin verilen adresler taranabilsin diye. Konuşmacı bunu "aptalca" bulup kaldırtıyor. Bu konuya aşağıda döneceğim.

## Arka planda ne oluyor

[28:00 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=1680s)

Docker'daki MCP sunucuları sürekli çalışmıyor: bir araç çağrıldığında konteyner açılıyor, iş bitince kapanıyor.

İki tür MCP sunucusu var. **Yerel** sunucular aynı bilgisayardaki süreçler arasında standart girdi-çıktı üzerinden konuşuyor: ağ yok, gecikme yok. **Uzak** sunucular ise internet üzerinden HTTP(S) ile erişiliyor; örneğin kripto para fiyatı veren CoinGecko sunucusu. Uzak sunucu işletmek ciddi iş: web sunucusu, kimlik doğrulama, güvenlik. Kendi bilgisayarında konteyner çalıştırmak çok daha basit.

## MCP geçidi

[32:51 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=1971s)

Normalde her MCP sunucusunu her uygulamaya ayrı ayrı tanımlarsın. Docker'ın **MCP geçidi** (gateway) bunu tek bağlantıya indiriyor: Claude ya da Cursor tek bir sunucuya bağlanıyor, o tek bağlantı arkadaki bütün sunuculara erişim veriyor. Gizli bilgiler de tek yerden yönetiliyor.

[35:53 · videoda dinle](https://www.youtube.com/watch?v=GuTcle5edjk&t=2153s)

Son gösterim: geçidi ağ üzerinden erişilebilir hâle getirip otomasyon aracı n8n'deki bir yapay zekâ ajanına bağlıyor. Ajan tek komutla üç aracı arka arkaya kullanıyor: en iyi restoranı bul, yanında Airbnb bul, sonucu Obsidian'a yaz.

---

## Bu kısım benim yorumum

**Bizde MCP zaten çalışıyor.** Gmail, Google Drive, Shopify, Supabase bağlantılarının hepsi MCP; Magnific de öyleydi. Bu video, o bağlantıların ne olduğunu anlamanı sağlıyor. Hangi bağlantı neye erişebiliyor, bilmen gerekiyor.

**Kali bölümündeki beyaz listeyi kaldırma.** Claude'un kendiliğinden koyduğu sınır doğru davranıştı; konuşmacının kaldırması yanlış. Kuzzat Altay'ın kitabındaki ilke burada geçerli: ajanın neye dokunabileceğini sen sınırlarsın. Tarama araçlarını yalnızca sana ait ya da yazılı izin aldığın sistemlerde kullan; başkasının sistemini izinsiz taramak yasa dışıdır.

**Asıl alınacak ders, kendi sunucunu yaptırmak.** Etsy'nin resmî bir MCP sunucusu yoksa, Etsy'nin API'si için kendi sunucunu yaptırabilirsin: "ürünleri listele, stok güncelle, siparişleri getir". Toggl örneğindeki üç kural geçerli: ne istediğini net tarif et, API belgesini ver, anahtarı koda yazma.

**Bir sınır:** API anahtarlarıyla çalışan her sunucu, o anahtarın yetkisi kadar güçlüdür. Kurmadan önce kodu okut, sadece okuma yetkisiyle başla.

---

*Kaynak: [you need to learn MCP RIGHT NOW!! — NetworkChuck, YouTube](https://www.youtube.com/watch?v=GuTcle5edjk). Otomatik altyazıdan ve konuşmacının kendi bölüm başlıklarından yazıldı; çeviri değil, Türkçe anlatım. Altyazıdaki bozulmalar düzeltildi: "cloud desktop" → Claude Desktop, "toggle" → Toggl, "NAN" → n8n, "end map" → nmap.*
