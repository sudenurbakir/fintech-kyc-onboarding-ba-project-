# Acceptance Criteria (Detaylı)

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0  
**Not:** Bu doküman, `epics-and-stories.md` dosyasındaki User Story’lerin detaylı kabul kriterlerini içerir.

---

## Epic 1: Kullanıcı Kaydı ve Telefon Doğrulama

### US 1.1 – Telefon Numarası ile Kayıt

**Acceptance Criteria:**

1. Kullanıcı telefon numarası alanına sadece rakam girebilmeli.
2. Numara formatı geçersizse (eksik/fazla haneli) “Geçerli bir telefon numarası giriniz” uyarısı gösterilmeli.
3. Geçerli numara girildiğinde “Devam Et” butonu aktif hale gelmeli.
4. Kullanıcı daha önce kayıt olmuş bir numara girerse, mevcut hesap akışına yönlendirilmeli.
5. “Devam Et” butonuna basıldığında loading göstergesi çıkmalı.

### US 1.2 – OTP Doğrulama

**Acceptance Criteria:**

1. OTP alanı 6 haneli olmalı ve sadece rakam kabul etmeli.
2. Kullanıcı 3 yanlış deneme hakkına sahip olmalı.
3. 3 yanlış denemeden sonra alan kilitlenmeli ve “Daha sonra tekrar deneyiniz” mesajı gösterilmeli.
4. OTP süresi 3 dakika olmalı. Süre dolduğunda “Kodun süresi doldu” mesajı + “Tekrar Gönder” butonu çıkmalı.
5. “Tekrar Gönder” butonu 60 saniye boyunca pasif olmalı.
6. Aynı numaraya 10 dakika içinde en fazla 3 OTP gönderilebilmeli (rate limit).
7. Doğru OTP girildiğinde bir sonraki adıma (Kimlik Belgesi) geçilmeli.

---

## Epic 2: Kimlik Belgesi Yükleme ve OCR

### US 2.1 – Belge Yükleme / Çekme

**Acceptance Criteria:**

1. Kullanıcıya iki seçenek sunulmalı: “Kamera ile Çek” ve “Galeriden Seç”.
2. Kamera izni daha önce reddedilmişse, açıklayıcı bir ekran gösterilmeli:
   - Başlık: “Kamera İzni Gerekli”
   - Açıklama: “Kimlik belgenizi tarayabilmek için kamera iznine ihtiyacımız var.”
   - Buton: “Ayarlara Git”
3. Kullanıcı belgeyi çektikten/seçtikten sonra önizleme ekranı gösterilmeli.
4. Önizlemede “Tekrar Çek” ve “Kullan” butonları olmalı.
5. Belge çok bulanıksa veya çok karanlıksa kullanıcıya uyarı verilmeli (opsiyonel kalite kontrolü).

### US 2.2 – OCR İşlemi

**Acceptance Criteria:**

1. Belge yüklendikten sonra “Belgeniz okunuyor...” loading ekranı gösterilmeli.
2. OCR başarılı olursa, okunan bilgiler (Ad, Soyad, Doğum Tarihi, Belge No vb.) kullanıcıya onay için gösterilmeli.
3. OCR başarısız olursa şu mesaj gösterilmeli:
   - “Belge net okunamadı. Lütfen daha iyi ışıkta ve düz bir zeminde tekrar deneyin.”
4. Kullanıcıya “Tekrar Dene” butonu sunulmalı.
5. 3 başarısız OCR denemesinden sonra “Manuel İnceleme Talep Et” seçeneği çıkmalı.
6. OCR işlemi 15 saniyeden uzun sürerse timeout mesajı gösterilmeli.

---

## Epic 3: Yüz Doğrulama

### US 3.1 – Selfie + Liveness + Eşleştirme

**Acceptance Criteria:**

1. Kullanıcıya yüzünü ekrandaki çerçeve içine alması için net görsel ve yazılı yönlendirme yapılmalı.
2. Liveness kontrolü aktif olmalı (kullanıcının canlı olduğu doğrulanmalı).
3. Yüz eşleştirme skoru yeterliyse bir sonraki adıma geçilmeli.
4. Eşleştirme başarısız olursa şu mesaj gösterilmeli:
   - “Yüzünüz kimlik belgesi ile eşleşmedi. Lütfen tekrar deneyin.”
5. Kullanıcıya maksimum 3 deneme hakkı verilmeli.
6. 3 başarısız denemeden sonra otomatik olarak Manuel İnceleme kuyruğuna alınmalı.
7. İşlem sırasında loading göstergesi olmalı.

---

## Epic 4: Sonuç ve Süreç Takibi

### US 4.1 – Sonuç Ekranı

**Acceptance Criteria:**

1. Üç farklı sonuç durumu net şekilde gösterilmeli:

   **Onaylandı:**
   - Başlık: “Kimlik Doğrulamanız Tamamlandı”
   - Mesaj: “Hesabınız aktif. Artık işlem yapabilirsiniz.”
   - Buton: “Ana Sayfaya Git”

   **Manuel İncelemede:**
   - Başlık: “İnceleme Sürecinde”
   - Mesaj: “Belgeleriniz inceleniyor. En kısa sürede bilgilendirileceksiniz.”
   - Buton: “Tamam”

   **Reddedildi:**
   - Başlık: “Doğrulama Tamamlanamadı”
   - Mesaj: “Kimlik doğrulamanız şu an için tamamlanamadı. Detaylı bilgi için destek ekibimizle iletişime geçebilirsiniz.”
   - Buton: “Destek Al” + “Tekrar Dene” (uygunsa)

2. Sonuç ekranı geri tuşu ile önceki adımlara dönülemeyecek şekilde tasarlanmalı.

### US 4.2 – Bildirimler

**Acceptance Criteria:**

1. Önemli durum değişikliklerinde (Onay, Red, Manuel İnceleme) push bildirim gönderilmeli.
2. Kullanıcı uygulamayı açtığında in-app bilgilendirme de gösterilmeli.
3. Bildirim metinleri net ve eyleme yönlendirici olmalı.

---

## Epic 5: Hata ve Edge Case Yönetimi

### US 5.1 – İnternet Bağlantısı Koptuğunda

**Acceptance Criteria:**

1. İnternet kesildiğinde kullanıcıya şu mesaj gösterilmeli:
   - “İnternet bağlantınız koptu. Lütfen bağlantınızı kontrol edin.”
2. “Tekrar Dene” butonu bulunmalı.
3. Bağlantı geri geldiğinde işlem kaldığı yerden devam edebilmeli (mümkün olan adımlarda).

### US 5.2 – Kamera İzni Reddedildiğinde

**Acceptance Criteria:**

1. Kamera izni reddedildiğinde özel bir bilgilendirme ekranı gösterilmeli.
2. Ekranda “Ayarlara Git” butonu olmalı ve cihaz ayarlarına yönlendirmeli.
3. İzin verilmeden süreç ilerletilememeli.
