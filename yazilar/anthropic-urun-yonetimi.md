# Veriyi Artık Kendisi Sorguluyor

**Anthropic'te bir ürün yöneticisi Claude'u günlük işinde nasıl kullanıyor: veri analizi, test senaryosu üretimi ve tek başına yapabileceklerin sınırının genişlemesi.**

---

*Kaynak: "How Anthropic uses Claude in Product Management" · Claude (Anthropic'in resmî YouTube kanalı) · 2 dk 57 sn · 26 Mart 2026 · 57 milyon izlenme. Konuşmacının adı videoda geçmiyor; Anthropic'te çalışan bir ürün yöneticisi.*

## Neden heyecanlı

[0:00 · videoda dinle](https://www.youtube.com/watch?v=91AJ0cpgLlQ&t=0s)

Konuşmacı, ürün yöneticiliğinde değişen şeyi hızla anlatıyor: artık çok daha hızlı deneyip değiştirebiliyor. Bir ürün fikrini, daha kimseyi işin içine katmadan Claude'la sınayabiliyor. Bunun sonucu bağımsızlık: başkasını beklemeden ilerleyebilmek.

## Asıl dert: veriye ulaşmak

[0:25 · videoda dinle](https://www.youtube.com/watch?v=91AJ0cpgLlQ&t=25s)

Ürün yöneticisinin bilinen bir sıkıntısı var: veri. Ya bir veri bilimcisine yazıp yardım istersin, ya da biraz SQL bilerek, yapısını tam tanımadığın bir veritabanını kendin sorgulamaya çalışırsın. İkisi de yavaş.

[0:44 · videoda dinle](https://www.youtube.com/watch?v=91AJ0cpgLlQ&t=44s)

Çözüm bir bağlantı oldu. Anthropic'in veri ekibi bir **BigQuery MCP'si** kurmuş: şirketin ürün verisi tablolarının hepsini Claude Code'a bağlayan bir köprü. Konuşmacının cümlesi işin özü: artık SQL yazmayı bilmen gerekmiyor; verinin ve sonucun **insan yorumcusu** olman yeterli.

## Canlı gösterim: karanlık mod ne kadar kullanılıyor

[1:07 · videoda dinle](https://www.youtube.com/watch?v=91AJ0cpgLlQ&t=67s)

Gösterim için gerçek veri değil, Claude'a önceden ürettirdiği **sentetik veri** kullanıyor: bir üründe açık mod ile karanlık mod kullanımı. Claude'a son üç ayda karanlık modun payını incelemek istediğini söylüyor ve hangi tabloya bakacağını belirtiyor.

Grafik açılıyor. Konuşmacıyı şaşırtan şey, istemediği eklemeler: 7 günlük hareketli ortalama, genel ortalama çizgisi. "Kendim yapsam bu kadar iyi olmazdı" diyor.

[1:38 · videoda dinle](https://www.youtube.com/watch?v=91AJ0cpgLlQ&t=98s)

Sonra bir adım ileri: aynı veriyi **plan türüne göre** ayırmasını istiyor. Claude dosyada değişiklik için izin istiyor, onay veriliyor, yeni grafik geliyor. Konuşmacının tahmini: tek başına yapsa saatler, belki daha fazla sürerdi.

## İkinci kullanım: değerlendirme testleri

[2:00 · videoda dinle](https://www.youtube.com/watch?v=91AJ0cpgLlQ&t=120s)

Ekibin Claude'u kullandığı ikinci yer **değerlendirme testleri** (evals): bir yapay zekâ ürününün doğru çalışıp çalışmadığını ölçmek için kullanılan örnek durumlar. Yöntem basit: Claude'a ürünün ne yapmaya çalıştığını ve bir iki örnek test durumunu veriyorsun, o bunları genişletiyor. Bir iki örnekten elli örneğe çok hızlı çıkılıyor.

## Neden önemli

[2:29 · videoda dinle](https://www.youtube.com/watch?v=91AJ0cpgLlQ&t=149s)

Konuşmacının umudu, ürün yöneticilerinin zamanını koordinasyon ve operasyondan çekip ürün stratejisine, müşteri görüşmelerine ve karar vermeye ayırabilmesi. Ama kapanışta daha önemli bir şey söylüyor: bu onun için otomasyondan fazlası. Claude, normalde tek başına yapamayacağı şeyleri yapabilmesini sağlıyor. Yani mevcut işi hızlandırmıyor yalnızca; yapabileceği işin sınırını genişletiyor.

---

## Bu kısım benim yorumum

Videonun bizim için en değerli cümlesi "verinin insan yorumcusu olman yeterli." Etsy mağazasında aynı durum var: satış raporları, görüntülenme, dönüşüm oranı, hangi ürünün hangi etiketle bulunduğu. Bu verileri CSV olarak indirip Claude'a verirsen, SQL bilmeden aynı soruları sorabilirsin: "son üç ayda hangi ürünlerin görüntülenmesi düştü?", "favoriye eklenip satılmayan ürünler hangileri?"

Bir uyarı: gösterimde sentetik veri kullanılıyor ve Claude'un istemeden eklediği şeyler bu sefer işe yarıyor. Gerçek veride bu eklemelerin doğru olup olmadığını kontrol etmek senin işin. "İnsan yorumcusu" olmak, sonuca bakıp mantıklı mı diye sorgulamak demek.

---

*Kaynak: [How Anthropic uses Claude in Product Management — Claude, YouTube](https://www.youtube.com/watch?v=91AJ0cpgLlQ). Otomatik altyazıdan yazıldı; altyazıdaki "e-bells" ifadesi "evals" (değerlendirme testleri) olarak düzeltildi.*
