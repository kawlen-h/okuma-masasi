# Kayak Kazasından Kesin Karara: Bir Prompt'un Adım Adım Kuruluşu

**Anthropic'in Applied AI ekibinden "Prompting 101": gerçek bir müşteri örneğinden uyarlanan bir sigorta görevinde, tek satırlık bir prompt'un kesin ve işlenebilir bir sonuca nasıl dönüştüğü.**

---

*Kaynak: Anthropic Applied AI ekibinden Hannah ve Christian'ın "Prompting 101" sunumu · 24 dk 47 sn. Türkçe altyazılı hâli @westkripto tarafından 11 Ağustos 2026'da X'te paylaşıldı (482 bin görüntülenme). Videonun sesi yerelde metne çevrildi; X videolarında saniye linki olmadığı için ara başlıklarda yalnızca zaman yazıyor.*

## Görev: kaza tutanağı ve el çizimi

*[0:00]*

Prompt mühendisliği, sunumdaki tanımıyla, dil modeline istediğimizi yaptırmak için açık talimat yazmak, ihtiyaç duyduğu bağlamı vermek ve bilgiyi en iyi sonucu verecek şekilde düzenlemek. Konuşmacılara göre bunu öğrenmenin en iyi yolu pratik.

Senaryo gerçek bir müşteriden uyarlanmış: bir **İsveç sigorta şirketi** her gün araç kazası başvurusu alıyor. Elinde iki belge var: İsveççe bir kaza tutanağı formu (17 onay kutulu, A aracı ve B aracı için iki sütun) ve kazayı tarif eden **elle çizilmiş bir kroki.** Hedef: Claude'un ikisine bakıp ne olduğunu ve kimin kusurlu olduğunu söylemesi.

**İlk deneme**, tek cümlelik bir prompt: "Bu kaza tutanağını incele, ne olduğunu ve kimin kusurlu olduğunu belirle." Sonuç: Claude bunun bir **kayak kazası** olduğunu düşünüyor. Konuşmacılar bunu modelin hatası saymıyor: prompt'ta neyin söz konusu olduğuna dair hiçbir şey yoktu. Ders şu: prompt mühendisliği deneyerek ilerleyen bir iş. "Claude bunun bir araç kazası olduğunu anlamalı" gibi bir test durumu yazarsın, prompt'u ona göre geliştirirsin.

## Önerilen yapı

*[3:30 civarı]*

Sohbette Claude'la karşılıklı konuşursun. Ama böyle bir görevde genelde API kullanılır ve hedef **tek mesajla işi ilk seferde doğru yaptırmak.** Önerilen sıra:

1. **Görev tanımı:** Claude ne için burada, rolü ne, bugün neyi başarmaya çalışıyor.
2. **İçerik:** bu örnekte form ve kroki; başka bir sistemden gelen veri de olabilir.
3. **Ayrıntılı talimatlar:** görevi nasıl ele alacağı, adım adım.
4. **Örnekler:** "şöyle bir içerik gelirse böyle cevap ver."
5. **Sonda hatırlatma:** kritik olan her şeyi tekrar et, sonra "şimdi işini yap" de.

## İkinci sürüm: bağlam ve ton

*[5:00]*

Christian prompt'a iki şey ekliyor. **Görev bağlamı:** "Bu sistem, İsveççe araç kazası tutanaklarını inceleyen bir sigorta uzmanına yardım ediyor; elle çizilmiş bir kroki de var." **Ton:** olgulara dayalı ve emin ol; emin değilsen değerlendirme yapma.

Sonuç daha iyi: Claude artık bunun bir araç kazası olduğunu anlıyor, A aracında 1. kutunun, B aracında 12. kutunun işaretli olduğunu okuyor. Ama kusur konusunda kesin bir şey söylemiyor, çünkü formun ne anlama geldiğine dair bilgisi eksik. Konuşmacılar bunu **iyi bir sonuç** sayıyor: talimata uyuyor, emin olmadığı şeyi uydurmuyor.

## Üçüncü sürüm: sabit bilgiyi sistem prompt'una koymak

*[7:30 civarı]*

Hannah'nın vurguladığı nokta: **form her seferinde aynı.** Doldurulma biçimi değişir, form değişmez. Bu tür bilgi sistem prompt'una konacak en iyi bilgi; sabit olduğu için prompt önbelleğe alma (prompt caching) için de ideal. Claude her seferinde formu yeniden çözmeye uğraşmaz, ne bekleyeceğini bilir.

*[10:00]*

Bilgiyi düzenlemek için **XML etiketleri** öneriliyor; Markdown da işe yarıyor ama XML etiketiyle içeriği adlandırabiliyorsun ("bunlar kullanıcı tercihleri") ve Claude ileride oraya geri dönebiliyor. Sistem prompt'una şunlar yazılıyor: formun başlığı, iki sütunun anlamı, 17 satırın her birinin anlamı ve **formun insanlar tarafından doldurulduğu**: kutuya çarpı yerine daire çizilebilir, karalama olabilir; her tür işarete bakılmalı.

Sonuç: Claude formu anlatmakla daha az vakit harcıyor, çünkü zaten biliyor; ve artık **B aracının kusurlu olduğunu** söylüyor.

## Örnekler ve konuşma geçmişi

*[12:00 civarı]*

Bu gösterimde kullanılmasa da iki güçlü araç anlatılıyor. **Örnekler** (few-shot): insanın sezgiyle doğru sonuca ulaştığı ama Claude'un zorlandığı gri durumları, görselleriyle ve nasıl çözüleceğinin açıklamasıyla sistem prompt'una koymak. Gerçek bir sigorta şirketi için onlarca, belki yüzlerce zor örnek. Döngü şu: uygulamanın nerede yanıldığını bul, o örneği prompt'a ekle; bir dahaki benzer durumda Claude ona başvursun.

*[15:00]*

**Konuşma geçmişi:** bu örnek arka planda çalışan bir sistem, kullanıcıyla konuşmuyor. Ama kullanıcıyla uzun konuşmalar yapan bir uygulamada, ilgili geçmiş bağlamı zenginleştirir.

## Dördüncü sürüm: adımların sırası

*[16:00 civarı]*

Sonda bir hatırlatma bölümü ekleniyor; amaçlardan biri **uydurmayı önlemek.** Hangi kutunun işaretli olduğu anlaşılmıyorsa Claude tahmin yürütmemeli; kroki bir insanın bile anlayamayacağı kadar kötüyse bunu söylemeli. Hatta her olgusal iddiada kanıtını göstermesi istenebilir: "B aracı sağa döndü, çünkü 2. kutu açıkça işaretli."

Burada sunumun belki de en önemli bulgusu geliyor: **Claude'un bilgiyi hangi sırayla incelediği çok önemli.** Bir insan da önce krokiye bakmaz; kutular ve çizgilerden oluşan anlamsız bir şeydir. Önce formu okursun, bunun bir araç kazası olduğunu ve hangi aracın ne yaptığını anlarsın; sonra krokiye bu bilgiyle bakarsın. Talimat buna göre yazılıyor: önce formu çok dikkatle incele, gördüklerini listele; sonra krokiye geç ve formdan öğrendiklerinle eşleştir.

Bir yan etki de gösteriliyor: "her kutuyu dikkatle incele" dediğin için Claude her kutuyu tek tek rapor ediyor. Bu istediğin şey olmayabilir. Prompt mühendisliğinde her talimatın çıktıya bir izi var.

## Beşinci sürüm: çıktı biçimi

*[20:09]*

Bir veri mühendisi açısından bütün bu açıklamalar güzel, ama sonunda sadece veritabanına yazılacak kararı istiyorsun. Son sürüme bir "önemli kurallar" bölümü ekleniyor: özet açık, kısa ve doğru olsun; değerlendirmeyi analiz edilen veriden başka hiçbir şey etkilemesin; **son kararı belirli bir XML etiketinin içine yaz.** Uygulama yalnızca o etiketi okuyor.

Gösterimin özeti konuşmacının kendi cümlesiyle: kayak kazasından başlayıp, emin olmayan çıktılardan geçip, üzerine gerçek bir uygulama kurulabilecek kesin ve biçimli bir sonuca gelindi.

## İki ek araç: ağza kelime koymak ve düşünme

*[22:00 civarı]*

**Önceden doldurulmuş cevap** (prefill): Claude'un cevabının nasıl başlayacağını sen yazarsın. JSON istiyorsan açılış süslü parantezini, XML istiyorsan açılış etiketini koyarsın; giriş cümleleri olmadan doğrudan istediğin biçimde devam eder.

**Genişletilmiş düşünme** (extended thinking): Claude'a cevap vermeden önce düşünme alanı vermek. Konuşmacıların önerisi ilginç: bunu prompt mühendisliğine **yardımcı bir araç** olarak kullan. Claude'un düşünme kaydını okuyup veriyi nasıl ele aldığını gör, işe yarayan adımları sistem prompt'una kalıcı olarak yaz. Hem daha az token harcarsın hem modelin nasıl düşündüğünü öğrenirsin.

---

## Bu kısım benim yorumum

**Bizim günlük görev metni bu yapıyla yazıldı:** görev bağlamı, sabit arka plan (onaylı kaynak listesi), adım adım talimat, kurallar, çıktı biçimi (JSON şeması). Videodaki "her kutuya bakınca her kutuyu raporlar" uyarısı orada da geçerli: "her kaynağı tara" dersen her kaynağı raporlar.

**Etsy listeleme prompt'u için şablon çıkıyor:**
- **Görev bağlamı:** "Türk edebiyatı temalı dijital ürünler satan bir Etsy mağazası için listeleme yazıyorsun."
- **Sabit arka plan:** mağazanın marka kuralları, ton, yasak kelimeler. Bunlar hiç değişmez, yani bir skill'in ya da sistem prompt'unun parçası olmalı.
- **Sıra:** önce ürün görseline bak, ne olduğunu ve kime hitap ettiğini listele; sonra anahtar kelimeleri seç; en son başlığı yaz.
- **Örnekler:** en iyi satan üç listelemen.
- **Çıktı:** başlık, 13 etiket ve açıklama, belirli bir biçimde.

**En çok işe yarayacak alışkanlık:** kötü bir sonuç aldığında modeli suçlamadan önce "kayak kazası" sorusunu sor: modele neyin söz konusu olduğunu söyledim mi?

---

*Kaynak: Anthropic, "Prompting 101" (Hannah ve Christian, Applied AI). Türkçe altyazılı paylaşım: [@westkripto, X](https://x.com/westkripto/status/2087165817309835607). Ses yerelde faster-whisper ile metne çevrildi; konuşmacıların söylemediği hiçbir şey eklenmedi.*
