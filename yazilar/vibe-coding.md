# Vibe Coding

**Kod yazmayı bilmeden yazılım üretmek: ne olduğu, nerede işe yaradığı, nasıl öğrenildiği.**

---

## Kavram nereden çıktı

Terimi Şubat 2025'te Andrej Karpathy ortaya attı. Karpathy OpenAI'ın kurucu ekibinden, Tesla'da yapay zekâ direktörlüğü yapmış biri. Tarif ettiği şey şuydu: ne istediğini düz dille söylüyorsun, model kodu yazıyor, sen değişiklikleri satır satır okumadan kabul ediyorsun. Hata çıkarsa hata mesajını olduğu gibi modele yapıştırıyorsun. Koda bakmıyorsun, akışa bırakıyorsun.

Karpathy bunu hafta sonu projeleri için, yarı şaka söylemişti. Terim hızla yayıldı ve anlamı genişledi. Bugün iki farklı şeyi anlatmak için kullanılıyor, ve ikisini ayırmak işin en önemli kısmı.

---

## İki ayrı şey: akışa bırakmak ve yönetmek

**Saf vibe coding:** Kodu hiç okumuyorsun. Sonuç çalışıyorsa tamam.

**Ajanla yazılım geliştirme:** Kodu sen yazmıyorsun ama sonucu sen yönetiyorsun. Ne istediğini tarif ediyorsun, çıkanı kontrol ediyorsun, neyin doğru olduğuna sen karar veriyorsun.

Programcı Simon Willison bu ayrımı net koydu: modelin yazdığı kodu okuyup anlıyor, test edip onaylıyorsan buna vibe coding denmez. O, yapay zekâyı hızlı bir yazım asistanı olarak kullanmaktır.

Senin için önemli olan ikincisi. Saf vibe coding bir hafta sonu oyuncağı için yeterli. Mağazana, müşteri verisine ya da paraya dokunan hiçbir şey için yeterli değil.

---

## Bu sitenin kendisi bir örnek

Okuduğun site vibe coding ile yapıldı. Sen ne istediğini Türkçe söyledin: "sol menü olsun", "telefonda okunsun", "Safari'deki gibi olsun". Kodu ben yazdım. Tek satır HTML yazmadın.

Süreç içinde vibe coding'in hem gücü hem tuzakları göründü:

- **Hız gerçekti.** Sol menü, arama, tema, okuma modu: her biri dakikalar içinde geldi.
- **Tarif belirsizse sonuç da belirsiz.** "Daha güzel yap" dediğinde bir yöne gittim, beğenmedin. "Safari'deki gibi" dediğinde tek seferde oturdu. Somut bir referans, sıfat yığınından iyidir.
- **Maliyet görünmez.** Sayfayı üç kez baştan yazdım, her biri binlerce token. Küçük değişiklikleri parça parça yapmaya geçince maliyet düştü. Bunu ekranda görmedin, ama faturada çıktı.
- **Kontrol etmezsen fark etmezsin.** Bir noktada kategorileri değiştirirken içerik listesi eski hâlinde kaldı ve sayfa tutarsızlaştı. Yayımlamadan önce fark edip düzelttim. Kontrol etmeseydim bozuk sürüm yayına giderdi.

---

## Nerede işe yarar, nerede duvara toslar

**İşe yaradığı yer:** Kendi kullanacağın araçlar. Prototipler. Tek seferlik betikler. Kişisel siteler. Bir fikri bir saatte görünür kılmak. Hatanın bedeli küçük olan her şey.

**Duvara tosladığı yer:**

- **Güvenlik.** Model API anahtarını koda gömebilir, şifreyi düz metin saklayabilir. Kodu okumuyorsan fark etmezsin.
- **Para ve kişisel veri.** Ödeme, müşteri adresi, mağaza hesabı. Buradaki hata geri alınamaz.
- **Uzun ömürlü kod.** Altı ay sonra bir şey bozulduğunda, hiç okumadığın kodu kimse düzeltemez — sen dahil.
- **Doğrulayamadığın şey.** Sonucun doğru olup olmadığını bilmiyorsan, model yanlışı da aynı özgüvenle sunar.

---

## Yeni başlayan biri neyi öğrenmeli

Çoğu kişi yanlış yerden başlıyor: "önce kod yazmayı öğrenmem lazım" diye düşünüyor. Vibe coding'de asıl beceri kod yazmak değil, **çıkanı değerlendirmek.**

### 1 · Tarif etmeyi öğren

İyi bir tarif üç şey içerir: **ne istiyorsun, neye benzesin, ne olmasın.** "Bir okuma sitesi yap" yerine: "Safari Reader gibi okuma modu, sol menü, telefonda tek sütun, magazin içerik olmasın." Referans ver: bir site, bir ekran görüntüsü, bir uygulama adı.

### 2 · Bağlamı yönet

Ajan her oturuma boş başlar. Projeyle ilgili kalıcı bilgileri bir dosyaya yaz; Claude'da bu dosyanın adı `CLAUDE.md`. Uzun oturumlarda model yorulmuş gibi görünür, aslında bağlam penceresi dolmuştur. O zaman bir devir notu iste ve yeni oturum aç. *Süper Yetenekli, Süper Aptal* yazısının ana konusu bu.

### 3 · Git'i geri alma düğmesi olarak öğren

Git'in bütün inceliklerine gerek yok. Üç şey yeter: değişikliği kaydet, geçmişe bak, eski hâle dön. Ajan bir şeyi bozduğunda geri dönebilmek, vibe coding'i korkusuz kılan şey.

### 4 · Okumayı öğren, yazmayı değil

Kodu yazabilmen gerekmiyor ama kabaca okuyabilmen gerekiyor: bu dosya ne yapıyor, burada bir şifre var mı, bu kısım dışarıya bir şey gönderiyor mu. Ajandan her değişikliği iki cümleyle açıklamasını iste. Zamanla okumayı öğrenirsin.

### 5 · Kontrol noktası koy

Ajanın "tamam, çalışıyor" demesi kanıt değil. Kendin aç, kendin dene. Yayına almadan önce *Lansman öncesi 20 maddelik kontrol* listesinden geçir. Ajan kendi işini kendisi onaylamamalı.

---

## Dört haftalık öğrenme yolu

**1. hafta:** İhtiyacın olan küçük bir şey yap. Etsy ürün açıklaması üreten bir sayfa, ya da beyit kartı oluşturan bir araç. Önemli olan, gerçekten kullanacağın bir şey olması.

**2. hafta:** Aynı şeyi boz ve düzelt. Ajana bir özellik ekletip sonra geri al. Git'le eski hâle dönmeyi dene.

**3. hafta:** Ajandan yaptığı her değişikliği açıklamasını iste. Anlamadığın her satırı sor.

**4. hafta:** İlk aracını 20 maddelik listeden geçir. Kaç maddeyi karşıladığını gör.

Bu siteyi okurken aynı anda bir şey üret. Uygulamadığın bilgi birikmez, sadece arşivlenir.

---

## Kısaca

Vibe coding gerçek bir beceri ve gerçekten hız kazandırır. Ama "kod yazmadan yazılım" vaadi yarım bir doğru: kodu sen yazmıyorsun, sonucun sorumluluğu yine sende. Ajan süper yetenekli bir yardımcı. Sınırları çizen, kontrol eden ve neyin doğru olduğuna karar veren sensin.

---

*Okuma Masası için özgün olarak yazıldı. Terimin kökeni Andrej Karpathy, Şubat 2025. Vibe coding ile yapay zekâ destekli programlama arasındaki ayrım Simon Willison'a ait.*
