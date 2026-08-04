# Edge Case Şablonu

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

---

## Kullanım Amacı
Yeni bir edge case / hata durumu tanımlanırken bu şablon kullanılır. Tutarlılık ve eksiksiz dokümantasyon sağlar.

---

## Edge Case Şablonu

**Edge Case ID:** [Örnek: EC-01]  
**Başlık:** [Kısa ve açıklayıcı başlık]  
**İlgili Adım / Ekran:** [Örnek: OCR İşlemi, Yüz Doğrulama, OTP vb.]  
**Öncelik:** Kritik / Yüksek / Orta / Düşük

### 1. Tetikleyici
[Ne zaman / hangi koşulda ortaya çıkar?]

### 2. Kullanıcıya Gösterilecek Mesaj / Ekran
[Kullanıcının göreceği net mesaj ve varsa butonlar]

### 3. Sistem Davranışı
[Sistem ne yapacak? (örnek: deneme hakkı azaltma, kuyruğa alma, loglama vb.)]

### 4. Kullanıcı Aksiyonları
[Kullanıcı ne yapabilir? (Tekrar Dene, Ayarlara Git, Destek Al vb.)]

### 5. Sonraki Adım / Çıkış Yolu
[Bu edge case’ten sonra süreç nasıl devam eder?]

### 6. İlgili User Story / Akış
[Hangi story veya akışla bağlantılı?]

### 7. Notlar
[Ek açıklamalar, teknik kısıtlar, Compliance notu vb.]

---

### Örnek Doldurulmuş Hali

**Edge Case ID:** EC-03  
**Başlık:** OCR Başarısız – Belge Okunamadı  
**İlgili Adım / Ekran:** OCR İşlemi  
**Öncelik:** Yüksek

**1. Tetikleyici**  
OCR motoru belgeyi yeterince yüksek güven skoru ile okuyamadığında (bulanıklık, yansıma, yanlış açı vb.)

**2. Kullanıcıya Gösterilecek Mesaj / Ekran**  
“Belge net okunamadı. Lütfen daha iyi ışıkta ve düz bir zeminde tekrar deneyin.”  
Butonlar: “Tekrar Dene”

**3. Sistem Davranışı**  
- Deneme sayısını 1 artırır  
- 3. başarısız denemeden sonra “Manuel İnceleme Talep Et” seçeneğini aktif eder  
- Hatayı loglar

**4. Kullanıcı Aksiyonları**  
- Tekrar Dene  
- (3. denemeden sonra) Manuel İnceleme Talep Et

**5. Sonraki Adım / Çıkış Yolu**  
- Başarılı olursa → Bilgi Onay ekranına geçer  
- 3. denemeden sonra manuel inceleme seçilirse → Manuel İnceleme sonucuna yönlendirilir

**6. İlgili User Story / Akış**  
US-2.2 (OCR İşlemi) + Alternative Flow AF-02

**7. Notlar**  
Kullanıcıya suçlayıcı dil kullanılmamalı. Çözüm odaklı mesaj tercih edilmeli.
