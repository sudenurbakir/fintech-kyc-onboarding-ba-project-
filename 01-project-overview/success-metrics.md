# Başarı Metrikleri (Success Metrics)

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

## 1. Ana Başarı Metrikleri (KPI)

| # | Metrik | Hedef | Ölçüm Yöntemi | Sıklık | Sorumlu |
|---|--------|-------|---------------|--------|---------|
| 1 | Onboarding Tamamlanma Oranı | ≥ %75 | Başarılı KYC / Başlayan kullanıcı sayısı | Haftalık | Product Owner |
| 2 | Ortalama KYC Süresi | ≤ 4 dakika | İlk adımdan onaylanmaya kadar geçen süre | Haftalık | Business Analyst |
| 3 | OCR Başarı Oranı | ≥ %90 | İlk denemede başarılı OCR / Toplam OCR denemesi | Haftalık | Backend + BA |
| 4 | Manuel İnceleme Oranı | ≤ %12 | Manuel kuyruğa düşen / Toplam KYC | Haftalık | Compliance + BA |
| 5 | Drop-off Oranı (Yarıda Bırakma) | ≤ %20 | Yarıda bırakılan / Başlayan kullanıcı | Haftalık | Product Owner |
| 6 | İlk Denemede Başarı Oranı | ≥ %70 | Tek seferde tamamlanan KYC / Toplam | Haftalık | Business Analyst |

## 2. Destekleyici Metrikler

| Metrik | Hedef | Açıklama |
|--------|-------|----------|
| OTP Doğrulama Başarı Oranı | ≥ %95 | Doğru girilen OTP oranı |
| Kamera İzni Verme Oranı | ≥ %85 | Kamera izni veren kullanıcı oranı |
| Ortalama Deneme Sayısı (OCR) | ≤ 1.4 | Kullanıcı başına ortalama OCR denemesi |
| Ortalama Deneme Sayısı (Yüz Doğrulama) | ≤ 1.3 | Kullanıcı başına ortalama yüz doğrulama denemesi |
| Destek Talebi Oranı | ≤ %5 | KYC sürecinden kaynaklı destek talebi / Toplam KYC |

## 3. Metrik Takip Notları

- Tüm metrikler **haftalık** olarak izlenecek ve Product Owner ile paylaşılacaktır.
- Hedeflerin altında kalınması durumunda kök neden analizi yapılacak ve aksiyon planı oluşturulacaktır.
- Özellikle **Drop-off Oranı** ve **Manuel İnceleme Oranı** birlikte değerlendirilmelidir (yüksek manuel inceleme drop-off’u artırabilir).
- Metrikler proje canlıya alındıktan sonra ilk 4 hafta boyunca yakından takip edilecektir.

## 4. Başarı Tanımı

Proje aşağıdaki koşulların **aynı anda** sağlanması durumunda başarılı kabul edilir:

- Onboarding tamamlanma oranı ≥ %75
- Ortalama KYC süresi ≤ 4 dakika
- Manuel inceleme oranı ≤ %12
- Drop-off oranı ≤ %20
