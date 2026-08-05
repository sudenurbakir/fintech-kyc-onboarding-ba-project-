# Multivariate Testing Teknikleri

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur BAkır - Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, A/B testten daha karmaşık olan Multivariate Testing (MVT) yaklaşımını ve onboarding sürecinde nasıl kullanılabileceğini açıklar.

---

## 2. Multivariate Testing Nedir?

Multivariate Testing, **birden fazla öğenin aynı anda** farklı kombinasyonlarının test edilmesidir.

- **A/B Test:** Tek bir değişkeni test eder (örnek: sadece bildirim başlığı).
- **Multivariate Test:** Birden fazla değişkeni aynı anda test eder (örnek: başlık + metin + gönderim zamanı).

Amaç: Hangi kombinasyonun en iyi performansı verdiğini bulmak.

---

## 3. Ne Zaman Kullanılmalı?

| Durum                              | A/B Test mi? | Multivariate Test mi? |
|------------------------------------|--------------|-----------------------|
| Tek bir metni test etmek           | Evet         | Hayır                 |
| Birden fazla öğeyi aynı anda test  | Hayır        | Evet                  |
| Trafik düşük                       | Evet         | Hayır (dikkatli)      |
| Trafik yüksek ve hızlı öğrenme isteniyorsa | -     | Evet                  |
| Öğeler birbirini etkiliyorsa       | -            | Evet                  |

**Not:** Multivariate testler daha fazla trafik gerektirir. Erken aşamada genellikle A/B test ile başlamak daha sağlıklıdır.

---

## 4. Onboarding İçin Uygun Multivariate Test Örnekleri

### Örnek 1: Hatırlatma Bildirimi

**Test edilecek öğeler:**
- Başlık (2 varyant)
- Metin (2 varyant)
- Gönderim zamanı (2 varyant)

**Toplam kombinasyon:** 2 × 2 × 2 = **8 varyant**

| Öğeler            | Varyant A                      | Varyant B                          |
|-------------------|--------------------------------|------------------------------------|
| Başlık            | Kimlik doğrulamanız eksik      | Hesabınızı tamamlayın              |
| Metin             | Kaldığınız yerden devam edin   | Hemen aktifleştirin                |
| Zamanlama         | 1 saat sonra                   | 3 saat sonra                       |

### Örnek 2: Belge Yükleme Ekranı

**Test edilecek öğeler:**
- Başlık metni
- Yönlendirme açıklaması
- Buton metni

Amaç: OCR’a geçiş oranını ve ilk denemede başarı oranını artırmak.

### Örnek 3: Sonuç Ekranı (Onaylandı)

**Test edilecek öğeler:**
- Başlık
- Açıklama metni
- Buton metni (“Ana Sayfaya Git” vs “Hesabımı Kullan”)

---

## 5. Multivariate Test Süreci

1. **Hedefi netleştir** (örnek: hatırlatma sonrası tamamlanma oranı)
2. **Test edilecek öğeleri seç** (çok fazla öğe seçme)
3. **Varyantları oluştur**
4. **Gerekli trafik miktarını hesapla**
5. **Testi başlat**
6. **Sonuçları analiz et** (hem tekil etki hem etkileşim etkisi)
7. **Kazanan kombinasyonu uygula**

---

## 6. Dikkat Edilmesi Gerekenler

| Konu                    | Açıklama                                                                 |
|-------------------------|--------------------------------------------------------------------------|
| Trafik ihtiyacı         | Kombinasyon sayısı arttıkça çok daha fazla kullanıcı gerekir             |
| Süre                    | A/B teste göre genellikle daha uzun sürer                                |
| Analiz karmaşıklığı     | Hangi öğenin asıl etki yarattığını ayırmak bazen zordur                  |
| Over-testing riski      | Çok fazla kombinasyon testi sonuçları anlamsız hale getirebilir          |
| Erken aşama önerisi     | İlk dönemlerde A/B test ile başlayıp, trafik arttıkça MVT’ye geçmek daha sağlıklıdır |

---

## 7. A/B vs Multivariate Karşılaştırma

| Kriter              | A/B Test                  | Multivariate Test              |
|---------------------|---------------------------|--------------------------------|
| Değişken sayısı     | 1                         | 2 veya daha fazla              |
| Trafik ihtiyacı     | Daha az                   | Daha fazla                     |
| Öğrenme hızı        | Daha hızlı                | Daha yavaş                     |
| Karmaşıklık         | Düşük                     | Yüksek                         |
| En iyi kullanım     | Hızlı doğrulama           | Öğeler arası etkileşimi anlama |

---

## 8. Öneri (Bu Proje İçin)

- **İlk 1-2 ay:** Sadece A/B test ile ilerle (bildirim metinleri, zamanlama, kritik ekran metinleri).
- **Trafik ve veri olgunlaşınca:** Özellikle bildirimler ve sonuç ekranları için Multivariate testlere geç.
- Her MVT sonrası öğrenilenleri dokümante et.

---

## 9. Notlar

- Multivariate testler güçlüdür ama yanlış kullanıldığında zaman ve trafik israfına yol açabilir.
- Business Analyst olarak test tasarımında “ne öğrenmek istiyoruz?” sorusunu net tutmak kritiktir.
- Bu doküman ilerleyen dönemde gerçek test sonuçlarıyla güncellenebilir.
