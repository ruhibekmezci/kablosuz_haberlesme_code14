# 📡 Kablosuz Haberleşme Path Loss (Yol Kaybı) Modelleri

Bu repo, kablosuz haberleşme sistemlerinde sinyal gücünün mesafeye ve ortam şartlarına bağlı olarak zayıflamasını (Path Loss) simüle eden MATLAB fonksiyonlarını ve test scriptlerini içerir. Kodlar, *MIMO-OFDM Wireless Communications with MATLAB* kitabındaki teorik modeller temel alınarak hazırlanmıştır.

## 📂 Dosya İçerikleri

Proje, 3 temel hesaplama fonksiyonu ve bunları görselleştiren 2 çalıştırma dosyasından oluşur.

### 1. Hesaplama Fonksiyonları
Bu fonksiyonlar, verilen parametrelere göre yol kaybını (dB cinsinden) hesaplar:

* **`PL_free.m` (Serbest Uzay Modeli):**
    * Engelsiz ortamda (Free Space) sinyal kaybını hesaplar.
    * Friis denklemine dayanır.
    * Kullanım: `PL = PL_free(fc, dist, Gt, Gr)`

* **`PL_Hata.m` (Hata Modeli):**
    * Şehirleşme yapısına göre (Büyük şehir, banliyö, açık alan) kaybı hesaplar.
    * **Önemli:** Fonksiyon frekansı Hz olarak alır ancak içeride MHz'e dönüştürerek işlem yapar.
    * Kullanım: `PL = PL_Hata(fc, d, htx, hrx, Etype)`

* **`PL_logdist_or_norm.m` (Log-Distance & Shadowing):**
    * Mesafeye bağlı logaritmik kaybın üzerine, ortamdaki rastgele engelleri (bina, ağaç vb.) simüle etmek için "Gölgeleme" (Shadowing) ekler.
    * Kullanım: `PL = PL_logdist_or_norm(fc, d, d0, n, sigma)`

### 2. Görselleştirme (Plot) Dosyaları
Modelleri test etmek ve grafikleri çizdirmek için bu dosyaları çalıştırın:

* **`plot_PL_general.m`**: Serbest Uzay, Log-Distance ve Log-Normal modellerini aynı anda çalıştırır ve yan yana 3 grafik çizer.
* **`plot_PL_Hata.m`**: Hata modelini; şehir (urban), banliyö (suburban) ve açık alan (open) senaryoları için çalıştırır ve karşılaştırmalı grafik verir.

## 🚀 Kurulum ve Kullanım

1.  Bu klasördeki tüm dosyaları MATLAB çalışma dizinine (Current Folder) indirin.
2.  MATLAB komut penceresine (Command Window) aşağıdaki komutlardan birini yazıp `Enter`a basın:

    ```matlab
    plot_PL_general
    ```
    *veya*
    ```matlab
    plot_PL_Hata
    ```

3.  Parametreleri değiştirmek için `.m` dosyalarını açıp `fc` (frekans), `htx` (verici yüksekliği) veya `distance` (mesafe) değişkenlerini düzenleyebilirsiniz.

## ⚠️ Dikkat Edilmesi Gerekenler

* **Frekans Birimi:** `PL_Hata.m` fonksiyonunu manuel kullanacaksanız, frekans değerini **Hz** cinsinden (örneğin `1.5e9` yani 1.5 GHz) girin. Kod, formüle uygulamadan önce bunu otomatik olarak MHz'e çevirir.

## 📚 Kaynakça
* *MIMO-OFDM Wireless Communications with MATLAB* - Yong Soo Cho, Jaekwon Kim, Won Young Yang, Chung G. Kang (2010, John Wiley & Sons)
