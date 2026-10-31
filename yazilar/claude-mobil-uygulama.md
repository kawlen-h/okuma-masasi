# Telefonda Çalışan Bir Uygulama, Dört Saatte

**Nick Saraev'in Claude Code ile mobil uygulama kursu: üç uygulama, beş adımlık tasarım çerçevesi, üç katmanlı test döngüsü, veritabanı, yapay zekâ özelliği, güvenlik denetimi ve App Store'a gönderme.**

---

*Kaynak: "How to Build Mobile Apps with Claude Code: Full Course (2026)" · Nick Saraev · YouTube · 4 sa 3 dk · 11 Mayıs 2026. Türkçe altyazılı hâlini @paramuhendisim X'te paylaşmıştı. Bu yazı orijinal kayıttan, otomatik altyazı okunarak yazıldı; altyazıda "Claude Code" sık sık "Cloud Code" diye geçiyor.*

> **Önce şunu bil:** Saraev videonun başında "ayda 300 bin dolar yapan bir işletmem var" diyor, sonunda da kendi ücretli topluluğu Maker School'u anlatıyor. Bu iddia kendi beyanı; doğrulanmış bir rakam değil. Kurs yöntem anlatıyor ve içerik sağlam. Ama "bu becerilerle para kazan" kısmı bir satış hunisi; onu ayrı tut.

## Ne yapıyor, nasıl kuruyor

[0:00 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=0s)

Kursun sözü şu: hiç mobil geliştirme deneyimin olmasa da kursun sonunda telefonunda çalışan gerçek bir uygulama olacak. Bu bir taslak ya da emülatör değil. Saraev'in koyduğu ön koşul tek: terminale İngilizce bir cümle yazabilmek. Üç uygulama yapıyor: bir alışkanlık takipçisi, fotoğraftan kalori hesaplayan bir uygulama ve ağaç büyüten bir Pomodoro sayacı. Sonra birini App Store'a gönderiyor.

Alışkanlık takipçisiyle başlamasının sebebi, bu tür uygulamaların insanların istediği temel işlevlerin çoğunu içermesi: veritabanına yazma ve okuma, bir arayüz, giriş sistemi. Kendi deyişiyle, alışkanlık takipçisi bir araç; asıl hedef değil. İlerleme sırası da öğretici: önce hiçbir dış servisi olmayan, veriyi cihazda tutan bir uygulama; sonra bir API; sonra veritabanı; en sonda giriş ekranı, bulut ve yapay zekâ.

[6:18 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=378s)

Kurulum basit. Claude'un Pro planı yeterli; Saraev Max kullanıyor. Claude Code'u web'de, masaüstü uygulamasında ya da bir kod editörünün içinde kullanabilirsin. O, Google'ın Antigravity editörüne "Claude Code for VS Code" eklentisini kuruyor; çünkü dosyaları solda görmek daha karmaşık işler yapmayı kolaylaştırıyor. Vurguladığı nokta şu: bunların hepsi aynı modelin etrafındaki farklı kabuklar.

## Hangi teknoloji: Expo ve React Native

[10:52 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=652s)

Bugün mobil uygulama yapmanın üç yaygın yolunu anlatıyor:

- **Expo + React Native** (onun seçimi): JavaScript/TypeScript ile tek bir kod tabanı yazıyorsun; aynı kod iOS'ta, Android'de ve web'de çalışıyor. Expo, derleme ve yayına hazırlama işini standart bir araca devrediyor. Telefonda anlık yenileme de var; test ederken çok işe yarıyor.
- **Flutter + Firebase**: Google'ın Dart dili ve hazır tasarım sistemi. Hızlı ama tasarımda seni Google'ın görünümüne kilitliyor.
- **Capacitor**: Bir web sitesi yapıp onu uygulama kabuğuna sarmak. En kolayı ama uygulama gibi değil, site gibi düşündürüyor.

Seçiminin gerekçesi: "Her şeyi baştan optimize etmeye çalışırsan hiçbir şeyde iyi olmazsın."

[15:54 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=954s)

Kurulum tek cümle: "Expo ve React Native ile mobil uygulama yapmak istiyorum, çalışma alanımı kur." Claude şablon indirmeden gerekli dosyaları kendisi oluşturuyor. Telefonda görmek için **Expo Go** uygulamasını indiriyorsun, bilgisayarda bir sunucu açılıyor ve ekrandaki QR kodu okutunca uygulama telefonunda açılıyor.

Burada önemli bir alışkanlık öğretiyor. Claude bazen "şu komutu çalıştır" diye işi sana devrediyor, çünkü eğitildiği kılavuzlar öyle yazılmış. Saraev'in tavsiyesi: "Bunu benim yerime yeni bir terminal penceresinde yap" de. İşin yüzde 80-90'ını bu şekilde Claude'a bırakabiliyorsun.

## İyi bir uygulamanın beş adımı

[24:02 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=1442s)

Kursun en kalıcı kısmı bu çerçeve. Kod yazmadan önce bu beş soruyu cevaplıyorsun:

1. **Çekirdek işlev.** Uygulamadan her şeyi söksen geriye ne kalır? Alışkanlık takipçisinde: bir alışkanlık oluşturup her dokunuşta kaydetmek.
2. **Çekirdek döngü.** Bir eylemi bir ödüle bağlayan, ideali 30 saniyenin altında süren döngü. Dokununca ses, titreşim, animasyon; hedef tamamlanınca konfeti. Örnek olarak Opal adlı uygulama engelleyiciyi veriyor: engellediğin her gün için verdiği taş giderek parlaklaşıyor. Saraev'e göre insan dokunsal bir canlı ve iyi uygulama bunu kullanıyor.
3. **Yan özellikler.** Döngüyü destekleyen ama değiştirmeyen şeyler: geçmiş kayıtlar ve grafik, günde bir kez yapılan alışkanlıklarla günde birkaç kez yapılanların ayrılması, belki sosyal özellik.
4. **Yüzey alanı kontrolü.** Yeni başlayanlar heyecanlanıp 10 işlev, 100 döngü ekliyor. Kural: **en fazla 5-7 ekran.** Kullanıcı bir kez gezince uygulamayı anlamalı.
5. **Geri getirme kancası.** Kullanıcının dönüp tamamlaması gereken yarım bir durum. Mesela onboarding'den sonra başlayan 3 günlük bir meydan okuma: tamamlamak için 72 saat içinde üç kez uygulamaya girmen gerekiyor.

Saraev beşinci adımı "kullanıcı davranışındaki karanlık kalıplardan yararlanmak" diye tarif ediyor. Bu dürüst bir itiraf ve üzerinde düşünmeye değer.

## Yapım: konuşarak geliştirmek

[33:45 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=2025s)

İlk taslak bitince `/init` komutunu çalıştırıyor. Bu komut, uygulamanın mimarisini, temasını ve dosya yollarını anlatan bir `CLAUDE.md` dosyası yazıyor. Böylece Claude her yeni oturumda bütün dosyaları baştan okumak zorunda kalmıyor; hem daha az token harcanıyor hem de Claude dosyaların nerede olduğunu biliyor. Sonra `/clear` ile sohbet geçmişini sıfırlıyor.

Talimatları klavyeyle yazmıyor, konuşuyor: Aqua adlı bir ses yazıya çevirme aracıyla beş adımlık çerçeveyi uzun bir paragraf hâlinde anlatıp yapıştırıyor. Claude işi dört aşamaya bölmeyi önerince verdiği cevap tipik: **"Hayır, hepsini yap."** Saraev'e göre Claude token tasarrufu için her zaman sonuna kadar zorlamıyor.

[37:49 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=2269s)

Sonrası bir döngü: uygulamayı Chrome'da aç, bak, gördüğün her sorunu sesli anlat, gönder. İlk turda yazı rengi arka planla aynı olduğu için metinlerin görünmemesi, yanlış hesaplanan yüzdeler ve tek bir hatırlatma saati gibi sorunlar çıktı. Bir de akıllıca bir istek ekledi: **geliştirici test ekranı.** 3 günlük meydan okumanın sonunda ne olduğunu görmek için üç gün beklemek yerine "meydan okumayı tamamlanmış say" düğmesi yaptırdı.

## Üç katmanlı test

[54:56 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=3296s)

Her değişiklikten sonra aynı sırayla test ediyor: **bilgisayarda Chrome**, sonra **telefon ekranını bilgisayara yansıtarak**, en son **gerçek telefonda.** Sebebi şu: bilgisayarda fareyle her yere eşit erişirsin, telefonda başparmakla. Titreşim, bildirim ve uzun basma gibi şeyleri ancak telefonda görürsün. Gerçekten de telefonda bilgisayarda görünmeyen sorunlar çıktı: emojilerin üst yarısı kesik görünüyordu, saat ve pil göstergesinin olduğu üst şerit tarihin üstüne biniyordu.

Hata gelince yaptığı şey basit: hata mesajının tamamını kopyalayıp Claude'a yapıştırıyor. Bir keresinde sorun koddan değil, tünel servisinin e-posta doğrulaması istemesinden kaynaklanıyordu; birkaç kez yapıştırınca Claude sebebi buldu. Bu kısmı videoda bırakmasının sebebi de güzel: "İşler göründüğünden zor. Bir hata çıkacak, soğukkanlı kal; sonuçta zeki bir kumla konuşuyorum."

[1:00:39 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=3639s)

Çalışan bir sürüm olunca iki şey yapıyor: `CLAUDE.md`'yi güncelliyor ve kodu **GitHub'a** gönderiyor. Yapay zekâ kod tabanında istediğini yaparken bir şey bozulursa, önceki sürüme dönebilmek hayat kurtarıyor.

## Veritabanı ve giriş: Supabase

[1:06:23 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=3983s)

Veri telefondayken uygulamayı başkasıyla paylaşamazsın ve aynı veriyi iki cihazda göremezsin. Çözüm bir veritabanı. Saraev Supabase kullanıyor; "en iyisi olduğu için değil, defalarca kullandığım için" diyor. Veritabanı eklediğin anda kullanıcıya da ihtiyaç duyuyorsun, çünkü sistem hangi verinin kime ait olduğunu bilmeli. Bu yüzden veritabanı ile giriş ekranı birlikte geliyor.

Mimari: veri **önce cihazda önbelleğe** yazılıyor, sonra arka planda veritabanıyla eşitleniyor. Böylece uygulama anında tepki veriyor, her dokunuşta sunucuyu beklemiyor. Saraev, ilk uygulamasında yalnızca veritabanı şemasını kurmanın üç haftasını aldığını anlatıyor; şimdi Claude bunu 30 saniyede yapıyor. Tablolar (alışkanlıklar, tamamlamalar, meydan okumalar, profiller) ve kullanıcılarla ilişkileri otomatik kuruluyor.

Bir ayrıntıya özellikle dikkat çekiyor: Supabase projesi açarken **"automatic RLS" kutusunu işaretle.** Satır düzeyinde güvenlik, kullanıcının yalnızca kendi satırlarını görmesini sağlıyor. Saraev'e göre bu kutu, yapay zekâyla yapılan pek çok uygulamanın verisi sızdığı için eklendi; ona göre varsayılan olarak açık gelmeli.

## Yapay zekâ özelliği: koç ve haftalık özet

[1:26:10 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=5170s)

İki özellik ekliyor. Biri **akıllı koçluk**: alışkanlık verisine bakıp "14 gündür uykunu tutturuyorsun ama su az, şunu dene" gibi kişisel bildirimler gönderiyor. Diğeri **haftalık ve aylık özet**: hangi alışkanlıkta ne kadar tutarlı olduğunu anlatan uzun bir değerlendirme.

Mimari, neredeyse her yapay zekâ özelliği için aynı: uygulama belirli aralıklarla bir **Supabase Edge Function** çağırıyor. Bu, sürekli açık bir sunucu değil; bir saniyeliğine açılıp işini yapan ve kapanan bir fonksiyon, bu yüzden çok ucuz. Fonksiyon veritabanından veriyi topluyor, bir prompt ile Claude API'ye gönderiyor (Sonnet modeli), cevabı veritabanına yazıyor ve uygulama bildirimi gösteriyor.

Burada iki iyi alışkanlık gösteriyor. Birincisi, **promptu kodlamadan önce örnek çıktı istemek**: 30 günlük sahte geçmiş oluşturtup on örnek mesaj ürettiriyor. Mesajlarda uzun tire (—) görünce promptu "uzun tire kullanma, çok yapay zekâ kokuyor" diye değiştiriyor; başlıklara emoji ekletiyor. İkincisi, **mesajları kuyruğa almak**: birbirinden bağımsız işleri Claude bir önceki işi bitirmeden gönderiyor.

API anahtarı konusunda kendisi söylüyor: anahtarı sohbete yapıştırmak yanlış, çünkü sohbet geçmişi bilgisayarda birçok yerde saklanıyor. Doğrusu anahtarı `.env` dosyasına koymak. Kendisi "tembellik ediyorum" deyip yine de sohbete yapıştırıyor.

## Güvenlik denetimi

[1:59:39 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=7179s)

Saraev'e göre yapay zekâyla uygulama yapanların yüzde 99'u bu adımı atlıyor, başarılı olanlar ise o yüzde 1'den çıkıyor. Risk somut: sızan API anahtarı yüzünden başkasının hesabına milyonlarca dolarlık kullanım yazılabilir. Sağlık ya da finans verisi tutuyorsan yasal sorumluluk da var.

Yöntemi: **temiz bir oturumda** (`/clear`) uzun bir güvenlik denetimi promptu çalıştırıyor. Prompt; uydurma paketleri, sunucu tarafında doğrulama eksikliğini, varsayılan olarak açık veritabanı kurallarını, koda gömülü gizli anahtarları ve tutarsız kimlik doğrulamayı arıyor. Bulguları kritik, yüksek, orta ve düşük olarak sıralıyor ve CWE (common weakness enumeration, yaygın zayıflık listesi) numarası veriyor. İlk turda "korumasız API uçları" ve "pahalı işlemler" gibi ciddi açıklar çıktı. Sonuncusu, bir saldırganın aynı isteği tekrar tekrar göndererek Claude faturasını şişirebileceği anlamına geliyor.

Sonra kritik bir adım geliyor: düzeltmelerden sonra **oturumu tekrar temizleyip aynı denetimi ikinci kez** çalıştırıyor. Sebebi, bir sorunu çözerken başka bir sorun yaratılabilmesi; önceki bağlamı bilmeyen yeni bir Claude bunu görebiliyor. Promptun kendisi videoda paylaşılmıyor; eski bir kursunun parçası olduğunu söylüyor.

## İkinci uygulama: fotoğraftan kalori

[2:08:09 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=7689s)

İkinci uygulamada süreci standartlaştırıyor: **fikir → yapım → tasarım → test (3 katman) → veritabanı → yeniden test → güvenlik → son test → yayın.** Bu sıra yeni bir özellik eklerken de aynı.

Örnek, Cal AI benzeri bir kalori takipçisi. Saraev, Cal AI'ın "sanırım 50-100 milyon dolara MyFitnessPal'a satıldığını" söylüyor; kendisi de emin değil. Yemeğin fotoğrafını çekiyorsun, yapay zekâ kaloriyi ve makroları tahmin ediyor. Dürüst bir not da düşüyor: bu tahminler artı eksi yüzde 10-15 hatalı olabilir; tabağın derinliği gibi şeyleri yapay zekâ bilemez. Bu yüzden kullanıcının sonucu düzeltebilmesi şart.

Kayda değer anlar:
- **Araştırma iste:** Onboarding'de boy ve kiloya göre kalori hedefi hesaplatırken "araştır, uydurma" diyor. Claude Mifflin-St Jeor denklemini kullanıyor.
- **Tasarımı sona bırakma ama veritabanından önce yap:** Veri yerelken tasarımı ve veri yapısını değiştirmek kolay; canlı veritabanında her değişiklik şema güncellemesi ve fazladan test demek.
- **Tasarım ilhamı:** Beğendiği uygulamanın ekran görüntüsünü verip "önce buna benzet, sonra farklılaştıracağım" diyor. Renk paletini bir renk ölçeği aracından alıyor, köşe yuvarlaklığını azaltıyor. Serif başlık fontunu deneyip beğenmiyor ve geri dönüyor.
- **Claude'a kendi ekran görüntüsünü aldırmak:** Hizalama sorunu düzelmeyince Chrome DevTools MCP ile Claude'a uygulamayı açtırıp her sayfanın ekran görüntüsünü aldırıyor, tutarsızlıkları listeletip düzelttiriyor.
- **Bağlam sınırı:** 200-250 bin tokendan sonra modelin ince değişikliklerde zorlandığını söylüyor; bu noktada `/compact` ile geçmişi sıkıştırıyor.
- **Hız:** Telefonda her kaydın yaklaşık bir saniye sürdüğünü fark edip Claude'a darboğazı sorduruyor. Mobil ağda gecikme yaklaşık 560 milisaniyeden 80'e iniyor. Kuralı: bilgisayarda nasıl hissettiriyorsa telefonda iki kat kötü hissettirir.

## Üçüncü uygulama: büyüyen ağaç

[2:59:22 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=10762s)

Pomodoro sayacında uygulama o kadar basit ki döngüyü tamamen görsellik taşıyor: oturuma başlayınca bir tohum ekiyorsun, 25 dakika boyunca gerçek zamanlı büyüyor, her oturum ormanına bir ağaç ekliyor. Geri getirme kancası şu: 72 saat gelmezsen ağaçlar solmaya başlıyor. Yalnızca iki ekran var.

Burada Claude'un **plan modu** devreye giriyor: Claude bir alt ajana animasyon kütüphanelerini araştırtıyor, sonra sorular soruyor (ağaç gerçek zamanlı mı büyüsün, veri nerede tutulsun, varsayılan süre ne olsun?). Claude'un çizdiği basit SVG ağaçlar zayıf kalınca, Saraev bir görsel üretme modeliyle uygulama maketleri ürettiriyor, ağaç ve arka plan görsellerini ayırtıyor ve Claude'a bunlardan uygulamayı yeniden kurduruyor.

## App Store'a gönderme

[3:45:02 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=13502s)

Saraev'in uyarısı şu: uygulamanın kabul edileceğinin garantisi yok, Apple'ın kuralları sıkı. Adımlar:

1. **Üretime hazırlık:** `app.json` ve `eas.json` dosyaları, 1024×1024 ikon, açılış ekranı, izin açıklamaları. Hepsini Claude yapıyor.
2. **Derleme:** Expo'nun bulut derleme servisi (EAS) uygulamayı "donduruyor". Ücretsiz katmanda sıra bekleniyor.
3. **Hesaplar:** Apple Developer hesabı ve Google Play Console. Google için ipucu: iş e-postasıyla kaydolmak doğrulamayı hızlandırıyor. Google ayrıca bir Android cihazda test etmeni istiyor.
4. **Gizlilik ve uyum:** En zahmetli adım. Gizlilik politikası ve destek sayfası olan, internetten erişilebilen bir web sayfası şart. Saraev Apple'ın yönergelerini Claude'a verip bu sayfaları yazdırıyor.
5. **Gönderim:** `eas submit --platform ios` komutu. Sonra App Store Connect'te iPhone ve iPad ekran görüntüleri, açıklama, anahtar kelimeler, yaş derecelendirmesi, fiyat ve **inceleme ekibi için bir test hesabı** gerekiyor.

Bir de tavsiye veriyor: doğrudan yayınlamak yerine önce **TestFlight** ile birkaç gerçek kullanıcıya gizlice dağıt.

[4:01:51 · videoda dinle](https://www.youtube.com/watch?v=BMMcmmnjrM8&t=14511s)

Son dört dakika Maker School reklamı: 90 gün içinde ilk müşterini bulamazsan para iadesi sözü veren bir topluluk.

---

## Bu kısım benim yorumum

**Beş adımlık çerçeve uygulama dışında da işe yarıyor.** Bir Etsy listelemesine ya da bir Shopify sayfasına da uygulanabilir: çekirdek işlev (ürün ne işe yarıyor), döngü (alıcıyı ne ödüllendiriyor), yan özellikler, yüzey alanı (sayfada gereksiz ne var), geri getirme (neden tekrar gelsin). Kurulda tartıştığımız "önce tek şeyi iyi yap" ilkesinin aynısı.

**Kursta güvenlikle çelişen üç alışkanlık var; bizde bunları yapmıyoruz:**
- **İzinleri tamamen kapatmak** ("dangerously skip permissions"): Claude'un her şeyi sormadan yapması hızlı ama bizim kurulumumuzda canlı kanala yazan her işlem önizleme, onay ve geri alma kuralına bağlı.
- **API anahtarını sohbete yapıştırmak:** Saraev yanlış olduğunu kendisi söylüyor. Anahtar yalnızca `.env` dosyasına gider ve sohbete hiç girmez.
- **Anthropic anahtarını uygulamanın içine koymak:** Kalori uygulamasında anahtar uygulama ayarlarında duruyor. Saraev'in de dediği gibi, gerçek üründe istek senin sunucundan geçmeli; anahtar uygulamaya gömülürse çıkarılıp kullanılabilir.

**İki kez denetim yöntemi değerli.** Temiz oturumda yapılan ikinci bir denetim, ilk düzeltmenin yarattığı yeni açığı yakalıyor. Bizdeki `guvenlik-denetimi` skill'ini de aynı şekilde iki kez, bağlamsız çalıştırmak mantıklı.

**Supabase RLS kısmı bizim için doğrudan geçerli.** Kendi projelerimizde zaten RLS kullanıyoruz; Saraev'in "RLS varsayılan olmalı" görüşü bizim kuralımızla aynı.

**Rakamlara mesafeli dur:** "Ayda 300 bin dolar", "Cal AI 50-100 milyona satıldı (sanırım)" ve "uygulama mağazasındakilerin yüzde 90'ından iyi" ifadeleri, konuşmacının doğrulanmamış iddiaları.

---

*Kaynak: [How to Build Mobile Apps with Claude Code: Full Course — Nick Saraev, YouTube](https://www.youtube.com/watch?v=BMMcmmnjrM8). 4 saatlik otomatik altyazı, 36 bölüm hâlinde okunarak yazıldı; çeviri değil, Türkçe anlatım.*
