# User Story Şablonu

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

---

## Kullanım Amacı
Bu şablon, yeni User Story yazarken tutarlı format sağlamak için kullanılır.

---

## User Story Şablonu

**Epic:** [İlgili Epic adı]  
**Story ID:** [Örnek: US-01]  
**Başlık:** [Kısa ve net başlık]

### User Story

**Olarak** [kullanıcı tipi]  
**İstiyorum** [amaç / istek]  
**Böylece** [elde edilecek fayda].

---

### Acceptance Criteria

1. [Test edilebilir kriter 1]
2. [Test edilebilir kriter 2]
3. [Test edilebilir kriter 3]
4. ...

---

### Detaylar / Notlar

- **Öncelik:** High / Medium / Low
- **Tahmini Efor:** [Story Point veya saat]
- **Bağımlılıklar:** [Varsa teknik veya iş bağımlılıkları]
- **Edge Case Referansı:** [İlgili edge case numarası]
- **Tasarım / Wireframe:** [Varsa link veya not]
- **Notlar:** [Ek açıklamalar]

---

### Örnek Doldurulmuş Hali

**Epic:** Kullanıcı Kaydı ve Telefon Doğrulama  
**Story ID:** US-1.2  
**Başlık:** OTP ile Telefon Doğrulama

**Olarak** yeni kullanıcı  
**İstiyorum** telefon numarama gelen OTP kodunu girerek doğrulama yapmak  
**Böylece** hesabımın bana ait olduğunu kanıtlayabileyim.

**Acceptance Criteria:**
1. OTP alanı 6 haneli olmalı ve sadece rakam kabul etmeli.
2. Kullanıcı 3 yanlış deneme hakkına sahip olmalı.
3. Süre dolduğunda “Tekrar Gönder” seçeneği sunulmalı.
4. Rate limit uygulanmalı (3 gönderim / 10 dakika).
5. Doğru OTP girildiğinde bir sonraki adıma geçilmeli.

**Detaylar / Notlar:**
- Öncelik: High
- Bağımlılıklar: SMS servisi
- Edge Case Referansı: #5 (OTP gelmedi / süre doldu)
