# Bir Dil Modeli Nasıl Yapılır

**Stanford CS229'un büyük dil modelleri dersi: ön eğitim, belirteçler, değerlendirme, veri, ölçekleme yasaları, ince ayar, insan geri bildirimiyle pekiştirme ve donanım tarafı — bir derste bütün resim.**

---

*Kaynak: "Stanford CS229 | Machine Learning | Building Large Language Models (LLMs)" · Stanford Online · 1 sa 44 dk · 27 Ağustos 2024 · 3,1 milyon izlenme. Türkçe altyazılı hâli @DeepTechTR tarafından X'te paylaşılmıştı. Dersi veren konuşmacının adı videoda geçmiyor; Stanford'da Alpaca, AlpacaFarm ve AlpacaEval çalışmalarının yazarlarından biri olduğunu kendisi anlatıyor. **Ders 2024 ortasından;** "bugünün en iyi açık modeli" gibi ifadeler o tarihin bilgisi.*

## Neler önemli: beş parça

[0:00 · videoda dinle](https://www.youtube.com/watch?v=9vM4p9NN0Ts&t=0s)

Bir dil modelini eğitirken beş şey önemli: **mimari** (bugün hepsi Transformer türevi), **eğitim kaybı ve algoritması**, **veri**, **değerlendirme** ve **sistemler**, yani bu dev modelleri donanımda verimli çalıştırmak.

Konuşmacının ilk dikkat çekici tespiti: akademi çoğunlukla mimariye ve kayıp fonksiyonlarına odaklanıyor — kendisi de kariyerinin büyük kısmında öyle yapmış. Ama pratikte önemli olan diğer üçü: **veri, değerlendirme ve sistemler.** Endüstri de bunlara odaklanıyor. Bu yüzden derste mimariyi hiç anlatmıyor.

Ders iki büyük bölüme ayrılıyor. **Ön eğitim** (pretraining): modeli kabaca bütün interneti modellemesi için eğitmek; GPT-2 ve GPT-3 bu dünyadan. **Son eğitim** (post-training): bu modeli bir yapay zekâ asistanına dönüştürmek; ChatGPT bu dünyadan.

## Dil modeli nedir

Dil modeli, kelime ya da belirteç dizileri üzerinde bir **olasılık dağılımı.** "The mouse ate the cheese" cümlesine yüksek olasılık verir. Dilbilgisi hatalı bir sürüme daha düşük verir: modelin sözdizimi bilgisi var. "The cheese ate the mouse" cümlesine de düşük verir: peynirlerin fare yemediğini biliyor, yani anlam bilgisi de var.

Bugünkü modeller **özbağlanımlı** (autoregressive): bir dizinin olasılığını, olasılığın zincir kuralıyla, "her kelimenin, öncekiler verildiğinde olasılığı"nın çarpımına ayırıyorlar. Görev basit: **bir sonraki kelimeyi tahmin et.** Bir dezavantajı var: üretim sırayla yapılıyor, yani uzun metin üretmek daha uzun sürüyor.

İşleyiş: metin belirteçlere bölünür, her birine bir numara verilir, model bir sonraki belirteç için bir olasılık dağılımı çıkarır, bundan örnek çekilir, numara metne geri çevrilir. Eğitimde ise modelin gerçek bir sonraki belirtece verdiği olasılık artırılır; bu da metnin olasılığını en üst düzeye çıkarmakla aynı şey.

## Belirteçler: kimsenin konuşmadığı önemli parça

Neden kelimeler değil? Yazım hatalı bir kelimenin karşılığı olmaz; Tayca gibi kelimeler arasında boşluk olmayan dillerde kelimeye bölmek mümkün değil. Neden harfler değil? Diziler çok uzar ve Transformer'ın maliyeti dizi uzunluğunun karesiyle büyür. Belirteç ikisinin ortası: ortalama **3-4 harf.**

En yaygın yöntemlerden biri **byte pair encoding**: her harf bir belirteçle başlar, en sık yan yana gelen çift birleştirilip yeni belirteç yapılır, bu tekrarlanır. "Tokenizer" kelimesi böylece "token" ve "izer" olarak ikiye bölünüyor. Küçük belirteçler de saklanıyor, ki yazım hataları da temsil edilebilsin. "Bank" kelimesinin para bankası mı nehir kıyısı mı olduğunu belirteç değil, Transformer bağlamdan çıkarıyor.

Bedeli de var. **Matematik:** "327" gibi bir sayı tek bir belirteç olabilir; model sayıları bizim gibi rakam rakam görmüyor, bu da aritmetiği zorlaştırıyor. **Kod:** Python'daki satır başı boşlukları eskiden garip işleniyordu; GPT-4'ün büyük değişikliklerinden biri kod için belirteçleri değiştirmek oldu.

## Değerlendirme

[16:00 civarı · videoda dinle](https://www.youtube.com/watch?v=9vM4p9NN0Ts&t=960s)

Geliştirme sırasında temel ölçü **şaşkınlık** (perplexity): ortalama belirteç kaybının üstel hâli. Sezgisi güzel: modelin her adımda **kaç belirteç arasında kararsız kaldığı.** 1 ile sözlük büyüklüğü arasında değişiyor. Standart bir veri kümesinde 2017'den 2023'e 70 civarından 10'un altına inmiş: model eskiden her kelimede 70 seçenek arasında bocalıyordu, şimdi 10'dan az.

Ama akademik karşılaştırmada artık kullanılmıyor, çünkü belirteç sistemine bağlı. Onun yerine birçok ölçütün toplandığı panolar var: Stanford'un HELM'i, Hugging Face'in açık model sıralaması. En yaygın ölçüt **MMLU**: tıptan astronomiye çoktan seçmeli sorular.

İki tuzak anlatıyor. Birincisi **ölçüm tutarsızlığı:** aynı model (Meta'nın ilk LLaMA 65B'si) bir panoda yüzde 63,7, başka birinde yüzde 48,8 almış — sadece değerlendirme yöntemi farklı olduğu için. İkincisi **test verisinin eğitime karışması:** model test sorularını eğitimde görmüş olabilir. Buna karşı zekice bir yöntem: internetteki veri kümeleri genelde karıştırılmamış oluyor; model test örneklerini orijinal sırayla, karışık sıradan daha olası buluyorsa, muhtemelen eğitimde görmüştür.

## Veri: "bütün internet" ne demek

[28:00 civarı · videoda dinle](https://www.youtube.com/watch?v=9vM4p9NN0Ts&t=1680s)

"Bütün internetle eğittik" kolay söyleniyor. Common Crawl gibi tarayıcılar yaklaşık **250 milyar sayfa, bir petabayt** veri topluyor. Rastgele bir sayfa ise bir felaket: HTML, yarım cümleler, menüler. Süreç şöyle:

1. **HTML'den metni çıkar.** Matematik formüllerini çıkarmak özellikle zor; forumların tekrar eden üst ve alt bilgilerini atmak gerekiyor.
2. **İstenmeyen içeriği ele:** zararlı içerik, kişisel bilgiler. Her şirketin çok uzun bir site kara listesi var.
3. **Tekrarları temizle:** farklı adreslerde aynı sayfa, binlerce kez kopyalanmış paragraflar.
4. **Kurallarla ele:** belirteç dağılımı tuhaf olan, kelimeleri anormal uzun olan, çok kısa ya da çok uzun sayfalar.
5. **Modelle ele:** Wikipedia'nın kaynak gösterdiği sayfalar muhtemelen kalitelidir. Bir sınıflandırıcıyı "bu sayfa Wikipedia'nın atıf yaptığı türden mi?" diye eğitip o tür sayfalardan daha fazla alıyorsun.
6. **Alanları dengele:** kod verisini artırmak akıl yürütmeyi iyileştiriyor, kitaplar da artırılıyor; eğlence içeriği azaltılıyor.
7. **Eğitimin sonunda en kaliteli veri:** öğrenme hızı düşerken Wikipedia ve insan eliyle toplanmış veri.

Ölçek de çarpıcı: veri kümeleri 150 milyar belirteçten **15 trilyona** çıkmış (LLaMA 3). Meta'nın yaklaşık 70 kişilik LLaMA ekibinde konuşmacının tahminine göre 15 kişi veriyle uğraşıyor. Konuşmacıya göre şirketler veri konusunda iki sebeple ketum: rekabet ve telif. Konuşmacı kitaplarla eğittiklerini söylemek istemediklerini, çünkü dava edilebileceklerini açıkça söylüyor.

## Ölçekleme yasaları

[42:00 civarı · videoda dinle](https://www.youtube.com/watch?v=9vM4p9NN0Ts&t=2520s)

Makine öğrenmesi derslerinde aşırı öğrenme (overfitting) öğretilir. Büyük dil modellerinde öyle olmuyor: **daha çok veri ve daha büyük model, daha iyi performans.** Konuşmacının esprisi: "Ama sınavda aşırı öğrenme var."

Asıl şaşırtıcı olan, bunun **öngörülebilir** olması. OpenAI'ın 2020 tarihli çalışmasında hesaplama, veri ve parametre sayısı ile test kaybı logaritmik ölçekte düz bir çizgi oluşturuyor. Yani hesaplamayı ne kadar artırırsan kaybın ne kadar düşeceğini tahmin edebiliyorsun. Henüz bir düzleşme görülmemiş; çoğu kişi bir noktada düzleşeceğini düşünüyor ama ne zaman, bilinmiyor.

[45:02 · videoda dinle](https://www.youtube.com/watch?v=9vM4p9NN0Ts&t=2702s)

Pratik sonucu: bir ay için 10.000 GPU'n var, hangi modeli eğiteceksin? **Eski yol:** 30 modeli birer gün eğit, en iyisini seç; son model sadece bir gün eğitilmiş olur. **Yeni yol:** küçük modellerle farklı boyutlarda deney yap (30 günün 3'ü), ölçekleme yasasını çıkar, büyüyünce hangisinin en iyi olacağını tahmin et, son modeli 27 gün eğit. Transformer ile LSTM karşılaştırması bu şekilde yapılıyor; çizginin eğimi ve başlangıç noktası ayrı ayrı önemli.

Ve önemli bir gözlem: küçük mimari farklar çoğunlukla sadece başlangıç noktasını kaydırıyor — "on saat daha eğitsen kapanır." **İyi veri ise eğimin kendisini** değiştiriyor.

**Chinchilla** çalışması kaynakların nasıl bölüneceğini gösterdi: hesaplama açısından en verimli oran **her parametre için yaklaşık 20 belirteç.** Ama şirketler çalıştırma maliyetini de düşünüyor: küçük model kullanımda daha ucuz. Bunu hesaba katınca oran parametre başına 150 belirtece çıkıyor.

Konuşmacı Rich Sutton'ın 2019 tarihli **"Acı Ders"** (The Bitter Lesson) yazısını da anıyor: hesaplama hep artacağına göre, önemli olan hesaplamadan yararlanabilen mimariler; küçük mimari süsler değil. Tavsiyesi: "Fazla karmaşıklaştırma; basit şeyleri iyi yap ve ölçekle."

**Bir hesap örneği** (konuşmacının kendi kaba tahmini): LLaMA 3'ün 400 milyar parametreli modeli. Hesaplama yaklaşık 3,8×10²⁵ işlem. Bu, o dönem ABD'de 10²⁶ işlemin üstündeki modelleri özel denetime tabi tutan başkanlık kararnamesinin hemen altında. Kararname sonradan yürürlükten kaldırıldı. 16.000 H100 GPU, yaklaşık 70 gün, kiralama karşılığı kabaca 52 milyon dolar; maaşlarla birlikte yaklaşık 75 milyon dolar. Karbon: yaklaşık 4.000 ton, New York-Londra arası 2.000 gidiş-dönüş uçuş kadar. Her yeni nesilde hesaplama yaklaşık 10 katına çıkıyor.

## Son eğitim: dil modelinden asistana

[59:00 civarı · videoda dinle](https://www.youtube.com/watch?v=9vM4p9NN0Ts&t=3540s)

Saf bir dil modeli asistan değil. GPT-3'e "Ay'a inişi altı yaşındaki birine anlat" dersen, "Yerçekimini altı yaşındaki birine anlat" diye devam eder; çünkü internette bir sorunun ardından genelde benzer sorular sıralanır.

**Denetimli ince ayar** (SFT): önceden eğitilmiş modeli, insanların yazdığı ideal soru-cevap çiftleri üzerinde biraz daha eğitmek. Kayıp aynı, veri farklı. Konuşmacıya göre GPT-3'ten ChatGPT'ye sıçramanın anahtarı bu. İnsan verisi pahalı olduğu için Stanford'da **Alpaca**'yı yapmışlar: 175 insan yazımı örnekten, o zamanın en iyi modeline 52.000 benzer örnek ürettirip LLaMA 7B'yi bunlarla eğitmişler.

Şaşırtıcı bulgu (LIMA çalışması): ince ayar verisini **2.000'den 32.000'e çıkarmak neredeyse hiç fark etmiyor.** Açıklaması: ince ayar modele yeni bilgi öğretmiyor, **biçim** öğretiyor. Önceden eğitilmiş model internetteki bütün kullanıcıları modelliyor; kimi madde madde yazıyor, kimi soruyu cevaplıyor. İnce ayar modele "bu tür kullanıcı gibi davran" diyor. Bilgi zaten ön eğitimde.

## İnsan geri bildirimiyle pekiştirme

[1:08:00 civarı · videoda dinle](https://www.youtube.com/watch?v=9vM4p9NN0Ts&t=4080s)

İnce ayarın üç sorunu var. **İnsan yeteneğiyle sınırlı:** iyi bir kitabı tanırsın ama yazamazsın; insanlar iyiyi ayırt etmekte üretmekten daha iyi. **Uydurmaya yol açabilir:** insan, modelin hiç görmediği doğru bir kaynağı cevaba yazarsa, model açısından bu "makul görünen bir kaynak uydur" talimatı. **Pahalı.**

Çözüm **RLHF**: model aynı soruya iki cevap üretiyor, insan hangisinin daha iyi olduğunu seçiyor. Bu tercihlerden bir **ödül modeli** eğitiliyor, sonra dil modeli bu ödülü artıracak şekilde pekiştirmeli öğrenmeyle (PPO) eğitiliyor. ChatGPT'nin üç adımı tam olarak bu: ince ayar, ödül modeli, PPO. Konuşmacının uyarısı: pekiştirmeli öğrenme kâğıt üstünde güzel, pratikte çok dağınık.

[1:15:06 · videoda dinle](https://www.youtube.com/watch?v=9vM4p9NN0Ts&t=4506s)

Bir yıl önce yine Stanford'dan çıkan **DPO**, bunu sadeleştirdi: pekiştirmeli öğrenme yerine, tercih edilen cevabın olasılığını artır, tercih edilmeyeninkini azalt. Belirli varsayımlar altında aynı sonuca gidiyor ve çok daha basit; açık kaynak dünyasında artık standart.

**İnsan etiketlemenin sorunları:** yönergeler karmaşık, insanlar doğruluk yerine biçime bakıyor. En bilineni: **insanlar uzun cevabı seçiyor.** Bu yüzden RLHF arttıkça cevaplar uzuyor. Konuşmacının sözleri: "ChatGPT'nin upuzun cevaplarından sıkıldıysanız, sebebi bu." Bir de etik sorunu var: etiketleyiciler çoğu zaman düşük ücret alıyor ve çok miktarda zehirli içerikle uğraşmak zorunda kalıyor.

Ve şaşırtıcı bir sonuç: ikili bir tercihte insanlar, insan çoğunluğuyla yalnızca **yüzde 66** oranında hemfikir. Makalenin yazarları kendileri etiketlediğinde bile yüzde 67-68. Dil modelleri ise yaklaşık **50 kat daha ucuza** insan çoğunluğuyla daha yüksek uyum sağlıyor: biraz daha yanlı olabilirler, ama tutarlılar.

## Sohbet modelini değerlendirmek

[1:30:08 · videoda dinle](https://www.youtube.com/watch?v=9vM4p9NN0Ts&t=5408s)

Açık uçlu cevapların tek bir doğrusu yok; bu yüzden en güvenilir ölçüt **Chatbot Arena**: rastgele kullanıcılar iki modelle kör olarak konuşup hangisinin daha iyi olduğunu oyluyor. Sınırlaması: kullanıcılar çoğunlukla teknolojiye meraklı, sorular da ona göre.

Ucuz alternatif, yargıç olarak bir dil modeli: **AlpacaEval**, Chatbot Arena ile yüzde 98 korelasyon, üç dakikadan kısa, 10 dolardan ucuz. Ama yine **uzunluk yanlılığı:** GPT-4'ün kendisiyle karşılaştırması tanım gereği yüzde 50. Prompt'a "ayrıntılı yaz" denince yüzde 64,4'e çıkıyor, "kısa yaz" denince yüzde 20'ye düşüyor. Çözüm, istatistiksel olarak uzunluğu kontrol etmek.

## Sistemler

Hesaplama en büyük darboğaz ve GPU'yu satın almak bile kolay değil. GPU'lar aynı komutu birçok veride aynı anda çalıştırmak için yapılmış ve en çok matris çarpımında hızlı. Ama hesaplama gücü bellekten ve iletişimden hızlı gelişiyor; bu yüzden GPU'lar çoğu zaman veri bekliyor. Teorik kapasitenin yüzde 50'sini kullanmak "çok iyi" sayılıyor; Meta'nın LLaMA'da yüzde 45 civarında olduğunu söylüyor.

İki numara: **düşük hassasiyet** (hesaplamayı 16 bitle yap, ağırlıkları 32 bitte sakla; derin öğrenmede zaten çok gürültü var, 0,01 ile 0,015 arasındaki fark önemsiz) ve **işlem birleştirme** (her satırda veriyi belleğe gidip getirmek yerine hepsini tek seferde yapmak; PyTorch'ta `torch.compile` modeli yaklaşık iki kat hızlandırıyor).

---

## Bu kısım benim yorumum

**"İnce ayar biçim öğretir, bilgi öğretmez" bizim için en işe yarar cümle.** Claude'a prompt'ta örnek verdiğinde ona yeni bir gerçek öğretmiyorsun, **biçim** gösteriyorsun. Etsy listeleme örneklerin Claude'a nasıl bir başlık yazacağını gösterir; ama mağazana özgü bir bilgiyi (fiyat, ölçü, malzeme) her seferinde bağlam olarak vermen gerekir.

**Uzun cevap yanlılığının sebebi burada.** Global CLAUDE.md'de "varsayılan en fazla 6 satır" kuralı var. Bu kural tam da RLHF'nin bıraktığı bu eğilime karşı yazılmış.

**Claude'u yargıç olarak kullanırken dikkat:** iki Etsy başlığını Claude'a "hangisi daha iyi" diye sorarsan, uzun olanı seçme eğiliminde olabilir. Karşılaştırmayı aynı uzunluktaki seçenekler arasında yap.

**"Veri, mimariden önemli" ilkesinin bizdeki karşılığı:** iyi bir bağlam, kurnaz bir prompt numarasından daha değerli. Kuzzat Altay da bağlam mühendisliği bölümünde aynı şeyi söylüyor.

**Uydurmanın bir kaynağı da ince ayar:** modelin bilmediği doğru bir bilgiyi "söylemesi" öğretilince, bilmediği şeyi uydurmayı öğrenebiliyor. Bu da kaynak isteyip doğrulamanın neden şart olduğunu açıklıyor.

---

*Kaynak: [Stanford CS229 | Building Large Language Models (LLMs) — Stanford Online, YouTube](https://www.youtube.com/watch?v=9vM4p9NN0Ts). Otomatik altyazıdan, uzunluğu nedeniyle üç parçada okunarak yazıldı; çeviri değil, Türkçe anlatım. Ders sonunda önerilen Stanford dersleri: CS224N, CS324 ve dil modelini sıfırdan kurduğun CS336.*
