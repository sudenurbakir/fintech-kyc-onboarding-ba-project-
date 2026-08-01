# Happy Path – KYC Onboarding Akışı

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır Business Analyst  
**Versiyon:** 1.0

## 1. Akış Özeti

Bu doküman, kullanıcının hiçbir hata veya engelle karşılaşmadan KYC sürecini başarıyla tamamladığı **mutlu yolu (Happy Path)** tanımlar.

---

## 2. Happy Path Akış Diyagramı

```mermaid
flowchart TD
    A[Uygulama Açılışı] --> B[Telefon Numarası Girişi]
    B --> C[SMS OTP Gönderimi]
    C --> D[OTP Doğrulama]
    D --> E[Kimlik Belgesi Seçimi]
    E --> F[Belge Yükleme / Çekme]
    F --> G[OCR İşlemi]
    G --> H{OCR Başarılı mı?}
    H -->|Evet| I[Selfie / Yüz Doğrulama]
    H -->|Hayır| F
    I --> J{Yüz Eşleşmesi + Liveness Başarılı mı?}
    J -->|Evet| K[KYC Onaylandı]
    J -->|Hayır| L[Manuel İnceleme]
    K --> M[Hesap Aktif - Ana Sayfa]
    L --> N[Kullanıcıya Bilgilendirme]

## 3. Adım Adım Happy Path Açıklaması

| Adım | Ekran / Aksiyon              | Sistem Davranışı                          | Kullanıcı Aksiyonu                          |
|------|------------------------------|-------------------------------------------|---------------------------------------------|
| 1    | Uygulama Açılışı             | Karşılama ekranı gösterilir               | “Başla” veya “Kayıt Ol” butonuna tıklar     |
| 2    | Telefon Numarası Girişi      | Numara formatı kontrol edilir             | Geçerli telefon numarası girer              |
| 3    | SMS OTP Gönderimi            | 6 haneli OTP gönderilir                   | -                                           |
| 4    | OTP Doğrulama                | Kod kontrol edilir                        | Doğru OTP’yi girer                          |
| 5    | Kimlik Belgesi Seçimi        | Kamera / Galeri seçenekleri sunulur       | Belge yükleme yöntemini seçer               |
| 6    | Belge Yükleme                | Önizleme gösterilir                       | Belgeyi onaylar                             |
| 7    | OCR İşlemi                   | Belge otomatik okunur                     | -                                           |
| 8    | OCR Sonucu                   | Okunan bilgiler gösterilir                | Bilgileri onaylar                           |
| 9    | Yüz Doğrulama                | Selfie + Liveness + Eşleştirme yapılır    | Yönlendirmelere uyarak selfie çeker         |
| 10   | Sonuç                        | “Kimlik Doğrulamanız Tamamlandı” ekranı   | “Ana Sayfaya Git” butonuna tıklar           |

## 4. Happy Path Kabul Kriterleri

- Tüm adımlar sorunsuz tamamlanmalı.
- Kullanıcı hiçbir hata mesajı görmemeli.
- Süreç toplamda **4 dakikadan kısa** sürmeli.
- OCR ve yüz doğrulama **ilk denemede** başarılı olmalı.
- Sonuç ekranında hesap aktif hale gelmeli ve kullanıcı ana sayfaya yönlendirilmeli.

## 5. Notlar

- Bu akış, tüm teknik servislerin (OTP, OCR, Yüz Doğrulama) sorunsuz çalıştığı ideal durumu temsil eder.
- Gerçek hayatta bu akışın yanında birçok alternatif ve exception akış bulunur (bkz. `alternative-flows.md` ve `edge-cases-matrix.md`).


