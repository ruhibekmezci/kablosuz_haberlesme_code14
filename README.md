📡 Kablosuz Haberleşme Path Loss (Yol Kaybı) Modelleri
Selam, bu repo kablosuz haberleşmede sinyalin mesafe ve ortam şartlarına göre ne kadar zayıfladığını (Path Loss) hesaplayan MATLAB kodlarını içeriyor. "MIMO-OFDM Wireless Communications with MATLAB" kitabındaki örneklerin pratiğe dökülmüş hali, yani işin teorisi sağlam.

📂 Dosyalar ve Ne İşe Yaradıkları
Burada 3 temel fonksiyon, 2 tane de bunları çalıştırıp grafik çizen script var.

Fonksiyonlar (Hesap Kitap İşleri)
PL_free.m: En temel model. Ortamda hiç engel yokmuş gibi (Serbest Uzay/Free Space) kaybı hesaplar. Formül Friis denkleminden geliyor.

PL_Hata.m: Hata Modeli. Bu biraz daha gerçekçi; şehir merkezi (urban), banliyö (suburban) veya açık alan (open) gibi ortamları hesaba katar. Frekansı Hz olarak girsen de o içeride MHz'e çevirip işlemi yapıyor, kafan rahat olsun.

PL_logdist_or_norm.m: Log-Distance ve Gölgeleme (Shadowing) modeli. Mesafeye bağlı standart kaybın üstüne bir de rastgele gürültü (standart sapma ile) ekleyerek gerçek hayat şartlarını (bina engeli vs.) simüle eder.

Çalıştırma Dosyaları (Grafik Şov)
plot_PL_general.m: Serbest uzay, Log-distance ve Log-normal modellerini kıyaslayan grafikleri çizer. Hepsini yan yana görmek için bunu çalıştır.

plot_PL_Hata.m: Hata modelini çalıştırır. Şehir, banliyö ve açık alan arasındaki farkı tek grafikte gösterir.

🚀 Nasıl Kullanılır?
MATLAB'ı aç.

Tüm dosyaların aynı klasörde olduğundan emin ol.

Grafikleri görmek için plot_PL_general.m veya plot_PL_Hata.m dosyasını aç ve çalıştır (Run).

Kendi senaryonu denemek istersen scriptlerin içindeki frekans (fc), mesafe (distance) veya anten yüksekliklerini (htx, hrx) değiştirip tekrar bas.

⚠️ Ufak Bir Not
Hata Modeli (PL_Hata): Frekansı fonksiyona Hz cinsinden veriyorsun (mesela 1.5e9), o içeride MHz'e (1500) dönüştürüyor. Elle MHz'e çevirip girme, sonuç şaşar.

📚 Kaynak
Bu kodlar şu kitaptan referans alınmıştır:

MIMO-OFDM Wireless Communications with MATLAB - Yong Soo Cho, Jaekwon Kim, Won Young Yang, Chung G. Kang (2010, Wiley).
