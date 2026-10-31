# Sohbet Botundan Ajana: Üç Basamak

**Teknik geçmişi olmayan biri için yapay zekâ ajanının ne olduğu: dil modeli, yapay zekâ iş akışı ve ajan arasındaki fark, gündelik örneklerle.**

---

*Kaynak: "AI Agents, Clearly Explained" · Jeff Su · 10 dk 9 sn · 8 Nisan 2025 · 5,5 milyon izlenme. Konuşmacı videoyu kendisi gibi teknik geçmişi olmayan ama yapay zekâ araçlarını düzenli kullanan insanlar için hazırladığını söylüyor.*

## Neden bu video

[0:00 · videoda dinle](https://www.youtube.com/watch?v=FwOTs4UxQS4&t=0s)

Video, herkesin "ajan, ajansal, ajan iş akışı" deyip durduğu bir kolajla açılıyor. Jeff Su'nun iddiası şu: ajan anlatımlarının çoğu ya fazla teknik ya fazla yüzeysel. Kendisi bildiğimiz bir şeyden — ChatGPT'den — başlayıp üç basamakta ajana çıkıyor. Yolda geçen korkutucu terimlerin (RAG, ReAct) aslında düşündüğümüzden basit olduğunu da gösteriyor.

## Birinci basamak: büyük dil modeli

[1:04 · videoda dinle](https://www.youtube.com/watch?v=FwOTs4UxQS4&t=64s)

ChatGPT, Gemini ve Claude gibi sohbet botları **büyük dil modellerinin** (LLM) üzerine kurulu uygulamalar. Metin üretmekte ve düzenlemekte çok iyiler. Sen bir girdi veriyorsun, model eğitildiği veriye dayanarak bir çıktı üretiyor. Kahve buluşması isteyen bir e-posta yazdırırsın; model senin yazacağından çok daha kibar bir metin çıkarır.

Ama "bir sonraki kahve buluşmam ne zaman?" diye sorarsan başarısız olur, çünkü takvimine erişimi yok. Bu basit örnek dil modelinin iki temel özelliğini gösteriyor:

- **Özel bilgiyi bilmez.** Ne kadar çok veriyle eğitilmiş olursa olsun, senin kişisel bilgini ya da şirketin iç verisini bilmez.
- **Pasiftir.** Sen sormadan bir şey yapmaz; bekler ve cevap verir.

## İkinci basamak: yapay zekâ iş akışı

[2:17 · videoda dinle](https://www.youtube.com/watch?v=FwOTs4UxQS4&t=137s)

Şimdi modele bir kural veriyorsun: "Kişisel bir etkinlik sorduğumda önce Google Takvim'ime bak, sonra cevap ver." Artık buluşmayı doğru söyler. Ama ardından "o gün hava nasıl olacak?" diye sorarsan yine başarısız olur — çünkü ona çizdiğin yol hep takvime bakmak, takvimde de hava durumu yok.

İş akışının temel özelliği bu: **yalnızca insanın önceden çizdiği yolu izleyebilir.** Teknik adıyla bu yola "kontrol mantığı" (control logic) deniyor. Hava durumu servisine bağlansan, cevabı sesli okutsan, yüzlerce adım eklesen bile değişmez: kararı veren insan olduğu sürece bu bir iş akışıdır, ajan değil.

Burada çok kullanılan bir terimi de açıyor: **RAG** (retrieval augmented generation), yapay zekânın cevap vermeden önce bir şeye bakması — takvime, hava servisine. Yani RAG da bir iş akışı türü.

Gerçek örneği kendi kurduğu bir otomasyon: Google Sheets'te haber linkleri topluyor, Perplexity bunları özetliyor, Claude da onun yazdığı bir prompt'la LinkedIn ve Instagram gönderisi taslağı çıkarıyor; hepsi her sabah 8'de kendiliğinden çalışıyor. Ama çıkan gönderiyi beğenmezse — örneğin yeterince komik değilse — geri dönüp prompt'u **elle** düzeltmesi gerekiyor. Deneme yanılmayı yapan hâlâ o.

## Üçüncü basamak: yapay zekâ ajanı

[5:26 · videoda dinle](https://www.youtube.com/watch?v=FwOTs4UxQS4&t=326s)

Aynı örnekte insanın yaptığı iki şeyi ayırıyor. Birincisi **akıl yürütmek**: en iyi yol ne — önce haberleri topla, sonra özetle, sonra yaz. İkincisi **araçlarla eylemde bulunmak**: linkleri Sheets'e koy, Perplexity'yle özetle, Claude'la yaz.

Videonun kendisinin de "en önemli cümle" dediği yer burası: bir iş akışının ajana dönüşmesi için gereken tek büyük değişiklik, **karar veren insanın yerini bir dil modelinin alması.** Ajan kendisi düşünür — "makaleleri tek tek kopyalamak yerine linkleri toplayıp başka bir araçla çekmek daha kolay" — ve kendisi seçer — "kullanıcı Google hesabını zaten bağlamış, Sheets daha iyi."

Bu yüzden ajanların en yaygın düzenine **ReAct** deniyor: akıl yürüt (reason) ve eyle (act).

Üçüncü özellik **yinelemek.** Gönderiyi elle düzeltmeyi hatırlıyor musun? Ajan bunu kendisi yapar: kendi taslağını eleştirmesi için başka bir modeli devreye sokar, LinkedIn'in iyi uygulama kurallarına göre puanlatır, kurallar karşılanana kadar tekrar eder.

## Gerçek bir örnek

[7:48 · videoda dinle](https://www.youtube.com/watch?v=FwOTs4UxQS4&t=468s)

Yapay zekâ alanının önde gelen isimlerinden Andrew'un hazırladığı bir görüntü ajanı gösterimi: "kayakçı" diye arattığında ajan önce bir kayakçının neye benzediğini düşünüyor — karda, kayakların üzerinde hızla giden biri — sonra video görüntülerini tarayıp kayakçı olduğunu düşündüğü kesitleri bulup getiriyor. Etkileyici görünmeyebilir; ama normalde bir insanın görüntüleri önceden izleyip "kayakçı, dağ, kar" diye tek tek etiketlemesi gerekirdi.

## Özet

[9:10 · videoda dinle](https://www.youtube.com/watch?v=FwOTs4UxQS4&t=550s)

- **Dil modeli:** girdi verirsin, çıktı verir.
- **İş akışı:** girdi verirsin ve izleyeceği yolu sen çizersin; yol dış araçlardan bilgi çekmeyi içerebilir. Yolu çizen insandır.
- **Ajan:** bir **hedef** alır; nasıl ulaşacağını kendisi düşünür, araçlarla ara sonuç üretir, sonuca bakıp tekrar gerekip gerekmediğine karar verir ve hedefe ulaşan son çıktıyı üretir. Karar veren modeldir.

---

## Bu kısım benim yorumum

Bu ayrım, kurduğumuz şeyleri doğru adlandırmayı sağlıyor. Okuma Masası'nın günlük derlemesi bir **iş akışı**: her sabah aynı kaynaklara bak, en fazla yedi haber seç, şu şemaya yaz. Yolu biz çizdik. Ama bu konuşmada senin "evet yap" dediğin işlerin çoğunda Claude bir **ajan** gibi çalıştı: yt-dlp hata verince başka yol aradı, altyazıdaki hatayı yakalayıp düzeltti.

Pratik sonuç: güvenilirlik gereken yerde iş akışı, esneklik gereken yerde ajan. Etsy'de her ürün için aynı adımlar izlenecekse (görsel, başlık, etiket, açıklama) iş akışı daha güvenli. Rakip mağazaları araştırmak gibi her seferinde farklı yol gerektiren işlerde ajan daha iyi.

---

*Kaynak: [AI Agents, Clearly Explained — Jeff Su, YouTube](https://www.youtube.com/watch?v=FwOTs4UxQS4). Otomatik altyazıdan ve konuşmacının kendi bölüm başlıklarından yazıldı; çeviri değil, Türkçe anlatım. Altyazıda "Chachi BT" diye geçen ChatGPT, "claw" diye geçen Claude olarak düzeltildi. Videoda konuşmacının ücretsiz araç setine bir link var.*
