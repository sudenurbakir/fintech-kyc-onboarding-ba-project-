# Epic’ler ve User Story’ler

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

---

## Epic 1: Kullanıcı Kaydı ve Telefon Doğrulama

**Amaç:** Kullanıcının telefon numarası ile hızlı ve güvenli şekilde sisteme kaydolmasını sağlamak.

### User Story 1.1
**Olarak** yeni kullanıcı  
**İstiyorum** telefon numaramı girerek kayıt olmak  
**Böylece** hesabımı oluşturmaya başlayabileyim.

**Acceptance Criteria:**
- Kullanıcı geçerli bir telefon numarası girebilmeli
- Geçersiz formatta numara girildiğinde anlamlı hata mesajı gösterilmeli
- “Devam Et” butonu sadece geçerli numara girildiğinde aktif olmalı

### User Story 1.2
**Olarak** yeni kullanıcı  
**İstiyorum** telefon numarama gelen OTP kodunu girerek doğrulama yapmak  
**Böylece** hesabımın bana ait olduğunu kanıtlayabileyim.

**Acceptance Criteria:**
- OTP 6 haneli olmalı
- Kullanıcı 3 yanlış deneme hakkı olmalı
- Süre dolduğunda “Tekrar Gönder” seçeneği sunulmalı
- Rate limit uygulanmalı (örnek: 3 gönderim / 10 dakika)

---

## Epic 2: Kimlik Belgesi Yükleme ve OCR

**Amaç:** Kullanıcının kimlik belgesini hızlı ve doğru şekilde sisteme yüklemesini ve OCR ile bilgilerin okunmasını sağlamak.

### User Story 2.1
**Olarak** kullanıcı  
**İstiyorum** kimlik belgemı kamera ile çekmek veya galeriden seçmek  
**Böylece** kimlik doğrulama sürecine devam edebileyim.

**Acceptance Criteria:**
- Kullanıcı kamera veya galeri seçeneğini görebilmeli
- Kamera izni yoksa açıklayıcı bir ekran ve “Ayarlara Git” butonu gösterilmeli
- Belge net değilse kullanıcıya uyarı verilmeli

### User Story 2.2
**Olarak** kullanıcı  
**İstiyorum** yüklediğim belgenin otomatik olarak okunmasını  
**Böylece** bilgileri tek tek girmek zorunda kalmayayım.

**Acceptance Criteria:**
- OCR işlemi sırasında loading göstergesi olmalı
- OCR başarısız olursa kullanıcıya net hata mesajı ve tekrar deneme seçeneği sunulmalı
- 3 başarısız denemeden sonra manuel inceleme seçeneği önerilmeli

---

## Epic 3: Yüz Doğrulama (Selfie + Liveness)

**Amaç:** Kullanıcının gerçekten belgedeki kişi olduğunu ve canlı olduğunu doğrulamak.

### User Story 3.1
**Olarak** kullanıcı  
**İstiyorum** selfie çekerek yüz doğrulaması yapmak  
**Böylece** kimlik doğrulama sürecini tamamlayabileyim.

**Acceptance Criteria:**
- Kullanıcıya yüzünü çerçeve içine alması için net yönlendirme yapılmalı
- Liveness kontrolü (canlılık) yapılmalı
- Yüz eşleşmesi başarısız olursa kullanıcıya anlamlı geri bildirim verilmeli
- Maksimum 2–3 deneme hakkı olmalı

---

## Epic 4: Sonuç ve Süreç Takibi

**Amaç:** Kullanıcıya KYC sonucunu net bir şekilde göstermek ve süreci takip etmesini sağlamak.

### User Story 4.1
**Olarak** kullanıcı  
**İstiyorum** kimlik doğrulama sonucumu görmek  
**Böylece** hesabımın durumunu anlayabileyim.

**Acceptance Criteria:**
- Üç olası sonuç net gösterilmeli: Onaylandı / Manuel İncelemede / Reddedildi
- Her sonuç için açıklayıcı mesaj ve sonraki adım bilgisi olmalı
- Onaylanan kullanıcı ana sayfaya yönlendirilmeli

### User Story 4.2
**Olarak** kullanıcı  
**İstiyorum** süreçle ilgili bildirim almak  
**Böylece** ne olup bittiğini kaçırmayayım.

**Acceptance Criteria:**
- Önemli durum değişikliklerinde push bildirim gönderilmeli
- Kullanıcı bildirimleri kapatmış olsa bile in-app bilgilendirme gösterilmeli

---

## Epic 5: Hata ve Edge Case Yönetimi

**Amaç:** Beklenmeyen durumlarda kullanıcının süreci mümkün olduğunca sorunsuz devam ettirebilmesini sağlamak.

### User Story 5.1
**Olarak** kullanıcı  
**İstiyorum** internet bağlantım koptuğunda ne yapacağımı bilmek  
**Böylece** işlemi kaybetmeden devam edebileyim.

**Acceptance Criteria:**
- Offline durumda anlamlı mesaj gösterilmeli
- Bağlantı geldiğinde işlemin kaldığı yerden devam etmesi desteklenmeli

### User Story 5.2
**Olarak** kullanıcı  
**İstiyorum** kamera izni vermediğimde ne yapacağımı net görmek  
**Böylece** süreci nasıl devam ettireceğimi anlayabileyim.

**Acceptance Criteria:**
- İzin reddedildiğinde açıklayıcı ekran çıkmalı
- “Ayarlara Git” butonu çalışmalı
