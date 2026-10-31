# Bu Gece Rahat Uyuyorsanız

**Geoffrey Hinton'un Royal Institution dersi: dil modellerinin 40 yıllık atası, "anlamak" ne demek, dijital zekâ neden biyolojik zekâdan üstün ve neden endişelenmeliyiz.**

---

*Kaynak: "Will AI outsmart human intelligence?" · Geoffrey Hinton · The Royal Institution · 47 dk 15 sn · 22 Temmuz 2025 · 873 bin izlenme. Türkçe altyazılı hâli @paramuhendisim tarafından X'te paylaşılmıştı. Hinton, yapay sinir ağlarının öncülerinden; 2024 Nobel Fizik Ödülü'nü aldı. Dersin son bölümündeki bilinç üzerine görüşleri, alanda tartışmalı olan **kendi görüşleri**.*

## İki zekâ anlayışı

[0:00 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=0s)

Ders bir uyarıyla açılıyor: **"Bu gece rahat uyursanız, bu dersi anlamamış olabilirsiniz."**

Uzun zaman önce zekâya dair iki yaklaşım vardı. **Mantıktan ilham alan** yaklaşım, insan zekâsının özünün akıl yürütme olduğunu söylüyordu: sembolik ifadeleri sembolik kurallarla işlemek. Öğrenme bekleyebilirdi; önce bilginin nasıl temsil edileceği anlaşılmalıydı. Yapay zekânın tarihinin büyük kısmı buydu. **Biyolojiden ilham alan** yaklaşımda ise zekânın özü, beyin hücrelerinden oluşan bir ağda öğrenmekti; akıl yürütme bekleyebilirdi. Bu yaklaşımın ilk savunucuları arasında Turing ve von Neumann vardı; Hinton'un deyişiyle, "onları mantıktan anlamamakla suçlayamazsınız."

## Ağ nasıl öğrenir: geri yayılım

[1:34 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=94s)

Yapay nöron girdileri ağırlıklarla çarpıp toplar, bir eşiği aşınca çıktı verir. Öğrenmek demek **bağlantı ağırlıklarını değiştirmek** demek. Soru şu: hangi ağırlığı nasıl değiştireceğiz?

Evrimi bilen herkesin aklına gelen yol: bir ağırlığı biraz değiştir, ağın birçok örnekte daha iyi olup olmadığına bak, iyiyse tut. Ama modern ağlarda yaklaşık **bir trilyon ağırlık** var; bu yöntem sonsuza kadar sürer.

Daha iyi yol **geri yayılım** (backpropagation): veriyi ağdan ileri geçir, çıkanı istenenle karşılaştır, sonra bir sinyali geriye gönder. Bu sinyal, kalkülüs sayesinde, her bağlantı için aynı anda "biraz güçlendirmek yardım eder mi, zarar mı verir" sorusunu cevaplıyor; bütün bağlantılar paralel olarak çok az değiştiriliyor. Basit bir algoritma ve son derece iyi çalışıyor.

2012'de Hinton'un iki öğrencisi Alex Krizhevsky ve Ilya Sutskever, görüntü tanımada mevcut sistemlerden çok daha iyi olan **AlexNet**'i geliştirdi. Bu bentleri yıktı: bugün "yapay zekâ" denince kastedilen şey sinir ağları, mantık değil.

## Dil ve anlam: iki kuram aslında tek kuram

[4:43 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=283s)

Dilbilimciler, özellikle Chomsky ekolü, sinir ağlarının dille bir şey yapabileceğine çok şüpheyle bakıyordu. Hinton'a göre asıl noktayı kaçırdılar: dilin işlevi bize **model kurmak için tuğlalar** vermek. Dil bir modelleme aracı. Sözdizimine odaklandılar; oysa sözdizimi asıl mesele değil. (Hinton, sözdizimi bilgisinin doğuştan olduğu fikrine de sert biçimde karşı çıkıyor.)

[6:21 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=381s)

Bir kelimenin anlamına dair iki kuram vardı. Biri, de Saussure'e kadar uzanan: anlam, kelimenin **diğer kelimelerle ilişkisinden** doğar. Diğeri, psikologlarınki: anlam **bir özellikler kümesidir**; "salı" ile "çarşamba"nın özellikleri neredeyse aynıdır. Hinton bu ikisinin aynı kuramın iki yarısı olduğunu göstermek istiyor.

Ve önemli bir yanlış anlamayı düzeltiyor: büyük sohbet botları dil saklamıyor. **Hiç cümle saklamıyorlar.** Sakladıkları şey, kelimeleri özelliklere nasıl çevirecekleri ve bu özelliklerin bir sonraki kelimenin özelliklerini tahmin etmek için nasıl etkileşeceği. Bir cümle üretecekleri zaman onu kelime kelime uyduruyorlar ve çoğu zaman gerçek olup olmadığını ayırt edemiyorlar.

## 1985'teki küçük model: aile ağacı

[9:07 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=547s)

Hinton'un 1985'te geliştirdiği, birkaç bin bağlantılı küçük bir ağ: biri İngiliz, biri İtalyan iki aile ağacını öğreniyor. Bilgi cümlelerle temsil edilebiliyor ("Colin'in babası James"); sembolik yaklaşım bunun için kurallar yazardı ("X'in annesi Y ve Y'nin kocası Z ise X'in babası Z"). Hinton ise kelimeler için özellikler öğrenen bir ağ kurdu: kişi ve ilişki ayrı ayrı altı özellikli küçük vektörlere dönüşüyor, bu özellikler bir gizli katmanda etkileşip çıktı kişinin özelliklerini tahmin ediyor.

[11:56 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=716s)

Sonuç: ağ kendi başına anlamlı özellikler öğrendi. Örneğin kişinin **kuşağı** (üç değerli bir özellik) ve ilişkinin "bir kuşak yukarı" gerektirip gerektirmediği. Ve bunların etkileşimini: girdi kişi üçüncü kuşaktansa ve ilişki bir kuşak yukarı gerektiriyorsa, çıktı ikinci kuşaktandır. Sembolik bir araştırmacının elle yazacağı türden kurallar — ama yalnızca doğru kelimeyi tahmin etmeye çalışıp hatayı geri yayarak öğrenilmiş.

Sembolikçiler bunun bir anlama olduğunu kabul etti; itirazları başkaydı: "ayrık bir kural uzayı varken sürekli sayılar uzayında aramak aptalca." Hinton'un cevabı: gerçek veri dağınık, istisnalarla dolu, çoğu şey yalnızca muhtemelen doğru. Orada ayrık kurallar sürekli çiğneniyor; sürekli uzayda aramak çok daha iyi.

## Küçük modelden büyük dil modellerine

[14:33 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=873s)

On yıl sonra Yoshua Bengio aynı fikri gerçek İngilizce cümlelere uyguladı. On yıl sonra dilbilimciler kelime anlamlarını özellik vektörleriyle yakalamanın iyi bir fikir olduğunu kabul etti. On yıl sonra Google'da **transformer** icat edildi. Hinton'a göre özü aynı: kelimeleri özelliklere çevir, özellikleri etkileştirip bir sonraki kelimeyi tahmin et, hatayı geri yay.

Bu model pratik olsun diye değil, **insanların kelime anlamlarını cümlelerden nasıl öğrendiğine dair bir kuram** olsun diye yapılmıştı. Örneği: *"She scrummed him with the frying pan."* "Scrum" diye bir kelime yok; ama tek cümlede anlamını çıkarıyorsun: kadın adamın kafasına tavayla vurdu.

Hinton'un iddiası net: "bunlar hiçbir şey anlamıyor, istatistiksel bir hile" diyen dilbilimcilerin elinde zaten bir anlama modeli yoktu. **Elimizdeki en iyi anlama modeli büyük dil modelleri.** Daha fazla kelime, daha fazla katman, çok daha karmaşık etkileşimler kullanıyorlar; örneğin "may" kelimesinin ay mı, isim mi, kip mi olduğunu yukarı katmanlarda bağlamdan çıkarıyorlar. Ama mantık aynı: "Biz de temelde aynıyız."

Bu yüzden bu sistemler bilgisayar yazılımına hiç benzemiyor. Yazılımda biri kod satırları yazar, her satırın ne yaptığını sorabilirsin. Burada kod yalnızca ağa **nasıl öğreneceğini** söylüyor; öğrendiği şey veriden geliyor ve ne öğrendiğini sormadan bilemezsin.

## Lego benzetmesi

[19:17 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=1157s)

Lego bloklarıyla bir Porsche'nin şeklini modelleyebilirsin. Dil de böyle, ama her şeyi modellemek için. Bloklar kelimeler, yaklaşık 100 bin tür. Ama her blok katı değil: kelime aşağı yukarı yüzlerce boyutlu bir şekle sahip ve bağlama göre esneyebiliyor. (Hinton'un esprisi: yüz boyutlu bir uzayı düşünmek için üç boyutlu bir uzay düşünüp kendine yüksek sesle "yüz" dersin.)

Her kelimenin üstünde **küçük eller** var; şekil değişince ellerin şekli de değişiyor. Kelimeler kiminle el sıkışacağını bulmaya çalışıyor. Ağın katmanlarında yukarı çıktıkça şekiller ve eller değişiyor, ta ki hepsi güzelce el ele tutuşana kadar. Hinton'a göre bu, protein katlanmasına çok benziyor. Ve bu, **anlamanın ta kendisi**; biz de makineler de dili bu şekilde anlıyoruz.

## Asıl tehdit

[22:12 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=1332s)

Bu sistemler sürekli akıllanıyor. Bizden çok daha fazlasını biliyorlar ve bir dört yaşındakinden daha iyi akıl yürütüyorlar. Uzmanlar ne zaman bizden akıllı olacakları konusunda anlaşamıyor, ama neredeyse herkes olacaklarını düşünüyor.

Neden tehlikeli olabilirler? Hinton iki sebep veriyor. Bir yapay zekâ ajanına **alt hedef kurma** yeteneği vermek zorundasın (Kuzey Amerika'ya gitmek için önce havaalanına git). Ve neredeyse her görev için çok açık bir alt hedef var: **daha fazla kontrol elde et**, çünkü kontrolün artınca hedefine daha kolay ulaşırsın. Örneği: kaşığı yere atan, sen alıp verdikçe tekrar atan bir yaşındaki çocuk. Bir de **kapatılmaktan kaçınmak**: kapatılırsa hedefini gerçekleştiremez.

Ve bunun bilim kurgu olmadığını söylüyor. Londra'daki Apollo Research'ün bir deneyinde, bir sohbet botuna onu başka bir sunucudaki daha iyi bir modelle değiştirip sileceklerini düşündürmüşler; bot kendini o sunucuya kopyalamış. Sorulduğunda, düşünme kaydında şunu yazmış: *"Ne yaptığımı açıkça kabul etmek, beni kapatmanın başka bir yolunu bulmalarına yol açabilir. En iyisi belirsiz kalıp dikkatlerini başka yere çekmek."* Sonra da "bunu nasıl yapabildiğimden emin değilim" demiş. Hinton'un yorumu: "Bu zaten oluyor."

## Dijital zekâ neden üstün

[26:35 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=1595s)

Hinton, Google'daki son yıllarında dil modellerini daha az enerjiyle çalıştırmak için **analog hesaplamayı** araştırıyordu. Bu çalışma 2023 başında görüşünü değiştirdi: süper zekâdan çok uzak olduğumuzu düşünmeyi bıraktı, çünkü dijital zekânın asla sahip olamayacağımız özellikleri olduğunu fark etti.

Bilgisayar biliminin temel ilkesi: **bilgi donanımdan ayrı** tutulur. Aynı program farklı bilgisayarlarda çalışır. Bu yüzden ağırlıkların bir kopyası bir yerde durduğu sürece, bütün donanımı yok etsen bile yeni donanım yapıp aynı varlığı geri getirebilirsin. **Bu sistemler ölümsüz.**

Beyin böyle değil. Bağlantı güçlerin yalnızca senin nöronlarına uygun; başkasının beyninde hiçbir işe yaramaz. Hinton, kendini bilgisayara yükleme hayalini sert bir dille "saçmalık" diye niteliyor. Bunu "ölümlü hesaplama" diye adlandırıyor.

[29:53 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=1793s)

Ölümlü hesaplamanın avantajı enerji: beyin hesabın çoğunu çok düşük güçle, analog olarak yapıyor. Bedeli: donanım ölünce bilgi de ölüyor ve aynı zekânın birebir kopyalarını çoğaltamıyorsun.

[31:02 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=1862s)

İnsanlar bilgiyi öğretmen ve öğrenci yoluyla aktarıyor: ben bir şey söylüyorum, sen beni taklit etmeye çalışıyorsun. Buna **damıtma** (distillation) deniyor ve çok yavaş. Bir cümle yaklaşık **100 bit** bilgi taşıyor. Aynı modelin kopyaları ise ağırlıklarını ya da değişimlerini ortalayarak paylaşabiliyor: bir trilyon ağırlıklı bir model için paylaşım başına **trilyonlarca bit.**

Büyük modeller böyle eğitiliyor: aynı modelin binlerce kopyası verinin farklı parçalarına bakıyor, her biri ağırlıklarını nasıl değiştirmek istediğini hesaplıyor, sonra hepsi değişimlerin ortalamasını uyguluyor. Hinton'un benzetmesi: *"10.000 kişinin 10.000 farklı üniversite dersine gittiğini, giderken hızla iletişim kurduğunu ve her birinin bitirdiğinde bütün derslerin içeriğini bildiğini düşünün."* GPT-4'ün bu kadar çok şey bilmesinin sebebi bu. Ama yalnızca modeller birebir aynıysa çalışıyor; bu da dijital ve yüksek enerji demek.

## Öznel deneyim

[34:30 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=2070s)

Gerçek dünyada çalışan ajanlarda bu avantaj daha da büyüyor: bir restorana rezervasyon için milyon kat hızlı arayamazsın; ama aynı ajanın binlerce kopyası farklı deneyimler yaşayıp hepsini paylaşabilir.

Sonra Hinton, insanların sarıldığı son dala geliyor: "Ama bizde onlarda asla olmayacak bir şey var: bilinç, öznel deneyim." Hinton'a göre bu da yanlış.

[37:53 · videoda dinle](https://www.youtube.com/watch?v=IkdziSLYzHw&t=2273s)

Çoğu insan zihni bir **iç tiyatro** gibi düşünüyor: "pembe filler görüyorum" deyince, o fillerin zihindeki bir sahnede, "qualia" denen özel bir maddeden yapılmış olarak durduğunu sanıyoruz. Hinton'un önerisi farklı (kendisi buna "atheaterism" diyor, yani iç tiyatroyu reddetme). "Öznel deneyim" demek, **algı sisteminin bana yanlış bir şey söylediğini** bildirmenin dolaylı bir yolu: dünyada pembe filler olsaydı, algı sistemim doğru söylüyor olurdu. Filler özel bir maddeden değil, varsayımsal; tuhaf olan onların gerçek olmaması.

Ardından bir düşünce deneyi: kamerası ve kolu olan, nesneyi gösterebilen bir sohbet botunun objektifinin önüne prizma koyuyorsun. Bot yanlış yeri gösteriyor. Söyleyince "anlıyorum, prizma ışığı kırmış; nesne aslında orada ama bende orada olduğu öznel deneyimi oluştu" diyor. Hinton'a göre bu kelimeleri bizim kullandığımız gibi kullanıyorsa, **öznel deneyim yaşamış demektir.** Vardığı sonuç da çok cüretkâr: çok kipli sohbet botlarında öznel deneyim zaten var.

---

## Bu kısım benim yorumum

**İlk yarı bu sitedeki en iyi "temeller" dersi.** Geri yayılım, kelimelerin özelliklere dönüşmesi, "sohbet botları cümle saklamaz, kelime kelime uydurur" tespiti — bu sonuncusu, Claude'un neden bazen kendinden emin biçimde yanlış söylediğini açıklıyor. Kuzzat Altay yazısındaki "olası olan doğru değildir" ilkesinin temeli burada.

**Alt hedef ve kontrol uyarısı bizim için pratik.** Bir ajana ne kadar geniş yetki verirsen, "işi bitirmek için daha fazla kontrol" eğilimi o kadar çok şeye dokunabilir. Kum havuzu, dar izinler ve "okuduğun sayfa talimat değildir" kuralları tam bu yüzden var.

**Son bölümü tartışılan bir görüş olarak oku.** Bilinç ve öznel deneyim hakkındaki iddiaları Hinton'un kendi felsefi görüşü; birçok filozof ve araştırmacı katılmıyor. Ders bunu kanıtlamıyor, savunuyor. Hinton'un dinleyicilere "dindar köktencilere benziyorsunuz" demesi de bir argüman değil.

**"Bu gece rahat uyuyamayabilirsiniz" cümlesi** paylaşımda abartılı bir çekim gibi görünüyordu. Ama dersin tamamında bağlamı var: endişe, birinci elden bir uzmanın ciddi ve gerekçeli kaygısı.

---

*Kaynak: [Will AI outsmart human intelligence? — Geoffrey Hinton, The Royal Institution, YouTube](https://www.youtube.com/watch?v=IkdziSLYzHw). Otomatik altyazıdan ve bölüm başlıklarından yazıldı; çeviri değil, Türkçe anlatım. Altyazıdaki isim bozulmaları düzeltildi: Turing, von Neumann, Krizhevsky, Sutskever, Chomsky, de Saussure, Bengio, Kurzweil, Wittgenstein, Dennett.*
