# KYC Doğrulama API Entegrasyon Detayları

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, KYC sürecinde kullanılacak doğrulama servislerinin (OCR, Yüz Doğrulama, Liveness) entegrasyonu için Business Analyst seviyesinde gereksinimleri tanımlar. Teknik implementasyon detayları geliştirme ekibi tarafından belirlenecektir.

---

## 2. Entegrasyon Kapsamı

| Servis                  | Amaç                                      | Zorunlu mu? |
|-------------------------|-------------------------------------------|-------------|
| OCR (Belge Okuma)       | Kimlik belgesinden veri çıkarma           | Evet        |
| Yüz Eşleştirme          | Selfie ile kimlik fotoğrafını karşılaştırma | Evet      |
| Liveness (Canlılık)     | Kullanıcının canlı olduğunu doğrulama     | Evet        |
| OTP / SMS               | Telefon numarası doğrulama                | Evet        |
| Manuel İnceleme Kuyruğu | Otomatik karar verilemeyen vakalar        | Evet        |

---

## 3. Temel API Akışları 

### 3.1 Belge Yükleme + OCR

**İstek (Yüksek Seviye):**
- Belge görüntüsü (ön yüz, gerekirse arka yüz)
- Belge tipi (opsiyonel)
- Kullanıcı / session referansı

**Beklenen Cevap:**
- OCR başarı durumu (success / failed)
- Okunan alanlar (Ad, Soyad, Doğum Tarihi, Belge No, Son Geçerlilik Tarihi vb.)
- Güven skoru (confidence score)
- Hata kodu ve açıklaması (başarısızsa)

**İş Kuralları:**
- Güven skoru belirli eşiğin altındaysa “başarısız” kabul edilir.
- Okunan veriler kullanıcıya onay için gösterilmelidir.
- Timeout süresi net tanımlanmalıdır (önerilen: 15 saniye).

### 3.2 Yüz Doğrulama + Liveness

**İstek (Yüksek Seviye):**
- Selfie görüntüsü / video frame’leri
- Daha önce yüklenen kimlik belgesi referansı
- Liveness challenge tipi (varsa)

**Beklenen Cevap:**
- Liveness sonucu (passed / failed)
- Yüz eşleştirme skoru
- Genel karar (approved / rejected / manual_review)
- Hata kodu ve açıklaması

**İş Kuralları:**
- Hem liveness hem eşleştirme başarılı olmalıdır.
- Skor eşiğinin altında kalırsa otomatik onay verilmez.
- Maksimum deneme sayısı aşılırsa manuel incelemeye düşürülür.

---

## 4. Ortak API Gereksinimleri

| Gereksinim               | Açıklama                                                                 |
|--------------------------|--------------------------------------------------------------------------|
| Kimlik Doğrulama         | Tüm istekler güvenli şekilde kimlik doğrulanmış olmalıdır (token vb.)   |
| Idempotency              | Aynı isteğin tekrarında yan etki oluşmamalıdır                           |
| Timeout                  | Her kritik çağrı için net timeout tanımlanmalıdır                        |
| Retry Politikası         | Geçici hatalarda kontrollü yeniden deneme yapılabilmelidir               |
| Hata Kodları             | Anlamlı ve tutarlı hata kodları dönülmelidir                             |
| Loglama                  | Tüm kritik istek/cevaplar (kişisel veri maskelenerek) loglanmalıdır     |
| Veri Minimizasyonu       | Sadece gerekli alanlar gönderilmeli ve alınmalıdır                       |

---

## 5. Beklenen Durum / Sonuç Kodları

| Durum              | Açıklama                                      | Kullanıcıya Yansıma                  |
|--------------------|-----------------------------------------------|--------------------------------------|
| approved           | Otomatik onay                                 | Başarı ekranı                        |
| manual_review      | Manuel inceleme gerekli                       | “İnceleme sürecinde” ekranı          |
| rejected           | Red                                           | Red ekranı                           |
| failed_ocr         | Belge okunamadı                               | Tekrar deneme / yönlendirme          |
| failed_face_match  | Yüz eşleşmedi                                 | Tekrar deneme                        |
| failed_liveness    | Canlılık kontrolü başarısız                   | Tekrar deneme                        |
| timeout            | Servis zaman aşımı                            | Genel hata + tekrar dene             |
| service_unavailable| Servis geçici olarak kullanılamıyor           | Genel hata mesajı                    |

---

## 6. Hata Yönetimi Beklentileri

- Kullanıcıya teknik hata kodları gösterilmemelidir.
- Her hata durumunda anlaşılır ve çözüm odaklı mesaj verilmelidir.
- Kritik hatalarda (servis down, timeout) kullanıcıya “daha sonra tekrar deneyin” seçeneği sunulmalıdır.
- Belirli hata tipleri otomatik olarak manuel inceleme kuyruğuna alınmalıdır.

---

## 7. Non-Functional Gereksinimler

| Alan              | Beklenti                                      |
|-------------------|-----------------------------------------------|
| Performans        | OCR ve yüz doğrulama makul sürede tamamlanmalı |
| Güvenlik          | Veriler şifreli iletilmeli ve saklanmalıdır   |
| Erişilebilirlik   | Servis kesintisinde kontrollü hata yönetimi   |
| Ölçeklenebilirlik | Yoğun kayıt dönemlerinde stabil çalışmalı     |
| Denetlenebilirlik | Kararların neden alındığı izlenebilir olmalı  |

---

## 8. Business Analyst Kontrol Listesi

Entegrasyon öncesi netleştirilmesi gerekenler:

- [ ] Hangi alanların OCR’dan zorunlu olarak beklediği
- [ ] Güven skoru eşikleri (OCR + yüz eşleştirme)
- [ ] Maksimum deneme sayıları
- [ ] Timeout ve retry kuralları
- [ ] Manuel incelemeye düşme koşulları
- [ ] Red koşulları
- [ ] Loglama ve maskeleme kuralları
- [ ] Üçüncü taraf servis seviyesinde SLA beklentileri

---

## 9. Notlar

- Bu doküman iş gereksinimlerini tanımlar. Teknik API sözleşmesi (endpoint, payload, header vb.) geliştirme ekibi tarafından ayrıca hazırlanmalıdır.
- Üçüncü taraf bir KYC sağlayıcısı kullanılacaksa, sağlayıcı kapasitesi ve kısıtları Compliance ile birlikte değerlendirilmelidir.
- Tüm karar eşikleri Product Owner ve Compliance onayı ile netleştirilmelidir.
