# Business Requirements Document (BRD)
**Proje Adı:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC  
**Versiyon:** 1.0  
**Hazırlayan:** Sudenur Bakır – Business Analyst

## 1. Amaç
Kullanıcıların mobil uygulama üzerinden hızlı, güvenli ve yasal gerekliliklere uygun şekilde kimlik doğrulaması yaparak hesabını aktifleştirmesini sağlamak.

## 2. Kapsam
### Dahil
- Telefon numarası ile kayıt
- SMS OTP doğrulama
- Kimlik belgesi yükleme + OCR
- Yüz doğrulama (liveness + matching)
- Sonuç ekranları (Onay / Manuel İnceleme / Red)
- Push bildirimleri ile süreç takibi
- Temel edge case yönetimi

### Hariç
- Video KYC (canlı görüşme)
- Kurumsal (B2B) onboarding
- Üçüncü taraf banka entegrasyonları

## 3. Paydaşlar
| Rol | Sorumluluk |
|-----|------------|
| Product Owner | Önceliklendirme, kabul kriterleri |
| Business Analyst | Gereksinim, akış, edge case |
| UX/UI Designer | Ekran tasarımları |
| Backend / Mobile Team | Teknik implementasyon |
| Compliance | Uyumluluk kontrolü |
| QA | Test senaryoları |

## 4. Başarı Metrikleri (KPI)
- Onboarding tamamlanma oranı ≥ %75
- Ortalama KYC süresi ≤ 4 dakika
- OCR başarı oranı ≥ %90
- Manuel inceleme oranı ≤ %12
- Drop-off (yarıda bırakma) oranı ≤ %20

## 5. Varsayımlar & Kısıtlar
- Kullanıcı 18 yaş üzeri
- Sadece geçerli kimlik belgeleri kabul edilir
- Uygulama iOS + Android
- İnternet bağlantısı zorunlu (offline destek sınırlı)
