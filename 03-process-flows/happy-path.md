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
