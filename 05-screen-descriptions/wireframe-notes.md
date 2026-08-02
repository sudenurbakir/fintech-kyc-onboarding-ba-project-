# Ekran Açıklamaları (Wireframe Notes)

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, onboarding sürecindeki temel ekranların low-fidelity açıklamalarını içerir. UX/UI ekibinin tasarım sürecinde referans alması için hazırlanmıştır.

---

## 2. Ekran Listesi ve Açıklamaları

### 2.1 Karşılama / Başlangıç Ekranı
- **Amaç:** Kullanıcıyı onboarding sürecine yönlendirmek
- **İçerik:**
  - Uygulama logosu
  - Kısa karşılama metni (“Hesabınızı birkaç adımda oluşturun”)
  - “Başla” veya “Kayıt Ol” birincil butonu
  - “Zaten hesabım var” ikincil linki
- **Not:** Mümkün olduğunca sade tutulmalı, dikkat dağıtıcı unsur olmamalı.

### 2.2 Telefon Numarası Giriş Ekranı
- **Amaç:** Kullanıcının telefon numarasını almak
- **İçerik:**
  - Başlık: “Telefon Numaranızı Girin”
  - Telefon numarası input alanı (ülke kodu ile birlikte)
  - “Devam Et” butonu (numara geçerli değilse pasif)
  - Alt bilgi: “Numaranıza doğrulama kodu göndereceğiz”
- **Hata Durumu:** Geçersiz numara girildiğinde input altında kırmızı uyarı metni

### 2.3 OTP Doğrulama Ekranı
- **Amaç:** Telefon numarasının doğrulanması
- **İçerik:**
  - Başlık: “Doğrulama Kodunu Girin”
  - 6 haneli OTP input alanları
  - “Kod gelmedi mi? Tekrar Gönder” linki
  - Geri sayım süresi (örnek: 2:59)
  - “Doğrula” butonu
- **Hata Durumu:** Yanlış kod girildiğinde “Kod hatalı, tekrar deneyin” mesajı

### 2.4 Kimlik Belgesi Yükleme Ekranı
- **Amaç:** Kullanıcının kimlik belgesini sisteme yüklemesi
- **İçerik:**
  - Başlık: “Kimlik Belgenizi Yükleyin”
  - İki seçenek kartı:
    - “Kamera ile Çek”
    - “Galeriden Seç”
  - Kısa bilgilendirme metni (“Belgenizin ön yüzünü net şekilde yükleyin”)
- **İzin Reddi Durumu:** Kamera izni yoksa özel bilgilendirme ekranı + “Ayarlara Git” butonu

### 2.5 Belge Önizleme Ekranı
- **Amaç:** Yüklenen belgenin kontrol edilmesi
- **İçerik:**
  - Belge önizleme alanı
  - “Tekrar Çek” butonu
  - “Kullan” birincil butonu
- **Not:** Belge kalitesi düşükse uyarı gösterilebilir.

### 2.6 OCR İşlem Ekranı (Loading)
- **Amaç:** Belge okuma sürecini kullanıcıya göstermek
- **İçerik:**
  - Loading animasyonu
  - Metin: “Belgeniz okunuyor...”
  - İsteğe bağlı: “Bu işlem birkaç saniye sürebilir”
- **Not:** 15 saniyeden uzun sürerse timeout mesajı gösterilmeli.

### 2.7 OCR Sonuç / Bilgi Onay Ekranı
- **Amaç:** Okunan bilgilerin kullanıcı tarafından onaylanması
- **İçerik:**
  - Okunan alanlar (Ad, Soyad, Doğum Tarihi, Belge No vb.)
  - “Bilgiler doğru mu?” sorusu
  - “Onayla ve Devam Et” butonu
  - “Tekrar Dene” ikincil butonu

### 2.8 Yüz Doğrulama Ekranı
- **Amaç:** Selfie + Liveness + Eşleştirme
- **İçerik:**
  - Yüz çerçevesi (oval veya kare)
  - Yönlendirme metinleri (“Yüzünüzü çerçevenin içine alın”, “Hafifçe gülümseyin” vb.)
  - Canlılık kontrolü için animasyonlu yönlendirmeler
- **Hata Durumu:** Eşleşme başarısızsa “Tekrar Dene” seçeneği

### 2.9 Sonuç Ekranı – Onaylandı
- **İçerik:**
  - Başarı ikonu
  - Başlık: “Kimlik Doğrulamanız Tamamlandı”
  - Açıklama: “Hesabınız aktif. Artık işlem yapabilirsiniz.”
  - “Ana Sayfaya Git” butonu

### 2.10 Sonuç Ekranı – Manuel İnceleme
- **İçerik:**
  - Bilgi ikonu
  - Başlık: “İnceleme Sürecinde”
  - Açıklama: “Belgeleriniz inceleniyor. En kısa sürede bilgilendireceğiz.”
  - “Tamam” butonu

### 2.11 Sonuç Ekranı – Reddedildi
- **İçerik:**
  - Uyarı ikonu
  - Başlık: “Doğrulama Tamamlanamadı”
  - Açıklama: “Kimlik doğrulamanız şu an için tamamlanamadı.”
  - “Destek Al” ve (uygunsa) “Tekrar Dene” butonları

---

## 3. Genel Tasarım Notları

- Tüm ekranlarda geri tuşu davranışı net tanımlanmalıdır (özellikle sonuç ekranlarında geri gidilememeli).
- Loading ve hata durumları her kritik adımda düşünülmelidir.
- Butonlar net hiyerarşiye sahip olmalı (Primary / Secondary).
- Metinler kısa ve anlaşılır tutulmalıdır.
- Erişilebilirlik (accessibility) göz önünde bulundurulmalıdır.

---

## 4. Notlar

- Bu açıklamalar low-fidelity seviyededir. Detaylı tasarım UX/UI ekibi tarafından yapılacaktır.
- Ekran sıralaması Happy Path ve alternatif akışlarla uyumludur.
