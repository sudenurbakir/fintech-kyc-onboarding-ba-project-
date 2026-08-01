# Paydaşlar (Stakeholders)

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

## 1. Paydaş Listesi

| # | Rol | İsim / Takım | Etki Seviyesi | İlgi Seviyesi | Ana Sorumluluk |
|---|-----|--------------|---------------|---------------|----------------|
| 1 | Product Owner | Ürün Ekibi | Yüksek | Yüksek | Önceliklendirme, kabul kriterleri onayı, roadmap |
| 2 | Business Analyst | Sudenur Bakır | Yüksek | Yüksek | Gereksinim toplama, akış tasarımı, edge case yönetimi, dokümantasyon |
| 3 | UX/UI Designer | Tasarım Ekibi | Orta | Yüksek | Ekran tasarımları, kullanıcı deneyimi akışları, kullanılabilirlik |
| 4 | Mobile Developer (iOS/Android) | Mobil Ekip | Yüksek | Orta | Uygulama tarafı geliştirme, kamera/OCR entegrasyonu, izin yönetimi |
| 5 | Backend Developer | Backend Ekibi | Yüksek | Orta | API’ler, OCR servisi, yüz doğrulama servisi, OTP altyapısı |
| 6 | Compliance Officer | Uyumluluk Ekibi | Yüksek | Orta | Yasal gerekliliklerin kontrolü, risk değerlendirmesi |
| 7 | QA Engineer | Test Ekibi | Orta | Yüksek | Test senaryoları, edge case testleri, regresyon |
| 8 | Customer Support | Destek Ekibi | Düşük | Orta | Manuel inceleme süreçleri, kullanıcı şikayetleri |
| 9 | Security Specialist | Güvenlik Ekibi | Orta | Orta | Veri güvenliği, fraud kontrolleri |

## 2. Paydaş Etki-İlgi Matrisi

```mermaid
quadrantChart
    title Paydaş Etki - İlgi Matrisi
    x-axis Düşük İlgi --> Yüksek İlgi
    y-axis Düşük Etki --> Yüksek Etki
    quadrant-1 Yakın Yönetim
    quadrant-2 Aktif Dahil Et
    quadrant-3 İzle
    quadrant-4 Bilgilendir
    Product Owner: [0.85, 0.9]
    Business Analyst: [0.8, 0.85]
    UX/UI Designer: [0.7, 0.65]
    Mobile Developer: [0.55, 0.8]
    Backend Developer: [0.5, 0.75]
    Compliance Officer: [0.45, 0.8]
    QA Engineer: [0.7, 0.55]
    Customer Support: [0.4, 0.3]
    Security Specialist: [0.4, 0.5]
