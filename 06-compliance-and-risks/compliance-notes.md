# Uyumluluk Notları (Compliance Notes)

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, KYC onboarding sürecinde uyumluluk gereksinimlerinin genel olarak nasıl ele alınması gerektiğini özetler. Detaylı yasal değerlendirme Compliance ekibi tarafından yapılacaktır.

---

## 2. Temel Uyumluluk Prensipleri

| Prensip                        | Açıklama                                                                 | Uygulama Örneği                                      |
|--------------------------------|--------------------------------------------------------------------------|------------------------------------------------------|
| Kimlik Doğrulama Zorunluluğu   | Kullanıcı hesabı aktif edilmeden önce kimlik doğrulaması yapılmalıdır   | OCR + Yüz doğrulama + OTP zorunlu adımlardır         |
| Veri Minimizasyonu             | Sadece gerekli veriler toplanmalıdır                                    | Sadece kimlik doğrulama için gereken alanlar istenir |
| Şeffaflık                      | Kullanıcıya ne yapıldığı ve neden yapıldığı açıkça belirtilmelidir      | Her adımda kısa bilgilendirme metinleri              |
| Güvenli İşleme                 | Kimlik ve biyometrik veriler güvenli şekilde işlenmeli ve saklanmalıdır | Şifreli iletim, sınırlı erişim, loglama              |
| Manuel İnceleme İmkanı         | Otomatik sistemlerin yetersiz kaldığı durumlarda manuel kontrol olmalı  | 3 başarısız denemeden sonra manuel kuyruk            |
| Denetlenebilirlik              | Süreç adımları izlenebilir ve raporlanabilir olmalıdır                  | Tüm kritik adımlar loglanmalı                        |

---

## 3. Süreç Bazlı Uyumluluk Kontrolleri

### 3.1 Telefon Doğrulama
- Telefon numarası, kullanıcının kontrolünde olan bir iletişim kanalı olarak doğrulanmalıdır.
- OTP gönderim sıklığı sınırlandırılmalıdır (rate limit).
- Başarısız denemeler loglanmalıdır.

### 3.2 Kimlik Belgesi ve OCR
- Sadece desteklenen ve geçerli belge türleri kabul edilmelidir.
- OCR sonucu kullanıcıya gösterilerek onaylatılmalıdır.
- Belge kalitesi yetersizse süreç ilerletilmemelidir.
- Belge görüntüleri güvenli şekilde saklanmalı ve sadece yetkili kişiler erişebilmelidir.

### 3.3 Yüz Doğrulama
- Liveness (canlılık) kontrolü yapılmalıdır.
- Yüz eşleştirme skoru belirli bir eşiğin altında kalırsa otomatik onay verilmemelidir.
- Başarısız denemeler sınırlandırılmalı ve sonrasında manuel incelemeye yönlendirilmelidir.

### 3.4 Sonuç ve Karar
- Otomatik onay, manuel inceleme ve red kararları net kurallara bağlanmalıdır.
- Reddedilen kullanıcılara makul bir bilgilendirme yapılmalıdır.
- Manuel inceleme sürecinin azami tamamlanma süresi tanımlanmalıdır.

---

## 4. Veri İşleme ve Saklama Notları

- Kimlik belgesi görüntüleri ve biyometrik veriler sadece doğrulama amacıyla işlenmelidir.
- Saklama süreleri net tanımlanmalı ve süre sonunda silinme / anonimleştirme süreci kurulmalıdır.
- Verilere erişim rol bazlı olmalı ve erişim logları tutulmalıdır.
- Üçüncü taraf servisler (OCR, yüz doğrulama) kullanılıyorsa, veri işleme sözleşmeleri gözden geçirilmelidir.

---

## 5. Risk Azaltma Önerileri

| Risk                              | Öneri                                                      |
|-----------------------------------|------------------------------------------------------------|
| Sahte belge yükleme               | OCR + liveness + manuel inceleme kombinasyonu              |
| Başkasının kimliği ile işlem      | Yüz eşleştirme + liveness zorunluluğu                      |
| Çok sayıda başarısız deneme       | Deneme hakkı sınırı + otomatik manuel inceleme             |
| Veri sızıntısı                    | Şifreleme, erişim kontrolü, loglama                        |
| Kullanıcıya yetersiz bilgilendirme| Her kritik adımda açık ve anlaşılır metinler               |

---

## 6. Compliance ile İş Birliği Noktaları

Business Analyst olarak Compliance ekibi ile şu konularda mutlaka hizalanılmalıdır:

- Hangi belge türlerinin kabul edileceği
- Otomatik onay / manuel inceleme / red kuralları
- Saklama süreleri ve silme politikaları
- Üçüncü taraf servislerin kullanım şartları
- Kullanıcıya gösterilecek yasal bilgilendirme metinleri

---

## 7. Notlar

- Bu doküman genel bir çerçeve sunar. Kesin kurallar ve onaylar Compliance / Hukuk ekibi tarafından verilmelidir.
- Süreç tasarlanırken “güvenlik ve uyumluluk” ile “kullanıcı deneyimi” dengesi gözetilmelidir.
- Tüm kritik karar noktaları dokümante edilmeli ve denetimlere hazır tutulmalıdır.# Uyumluluk Notları (Compliance Notes)

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, KYC onboarding sürecinde uyumluluk gereksinimlerinin genel olarak nasıl ele alınması gerektiğini özetler. Detaylı yasal değerlendirme Compliance ekibi tarafından yapılacaktır.

---

## 2. Temel Uyumluluk Prensipleri

| Prensip                        | Açıklama                                                                 | Uygulama Örneği                                      |
|--------------------------------|--------------------------------------------------------------------------|------------------------------------------------------|
| Kimlik Doğrulama Zorunluluğu   | Kullanıcı hesabı aktif edilmeden önce kimlik doğrulaması yapılmalıdır   | OCR + Yüz doğrulama + OTP zorunlu adımlardır         |
| Veri Minimizasyonu             | Sadece gerekli veriler toplanmalıdır                                    | Sadece kimlik doğrulama için gereken alanlar istenir |
| Şeffaflık                      | Kullanıcıya ne yapıldığı ve neden yapıldığı açıkça belirtilmelidir      | Her adımda kısa bilgilendirme metinleri              |
| Güvenli İşleme                 | Kimlik ve biyometrik veriler güvenli şekilde işlenmeli ve saklanmalıdır | Şifreli iletim, sınırlı erişim, loglama              |
| Manuel İnceleme İmkanı         | Otomatik sistemlerin yetersiz kaldığı durumlarda manuel kontrol olmalı  | 3 başarısız denemeden sonra manuel kuyruk            |
| Denetlenebilirlik              | Süreç adımları izlenebilir ve raporlanabilir olmalıdır                  | Tüm kritik adımlar loglanmalı                        |

---

## 3. Süreç Bazlı Uyumluluk Kontrolleri

### 3.1 Telefon Doğrulama
- Telefon numarası, kullanıcının kontrolünde olan bir iletişim kanalı olarak doğrulanmalıdır.
- OTP gönderim sıklığı sınırlandırılmalıdır (rate limit).
- Başarısız denemeler loglanmalıdır.

### 3.2 Kimlik Belgesi ve OCR
- Sadece desteklenen ve geçerli belge türleri kabul edilmelidir.
- OCR sonucu kullanıcıya gösterilerek onaylatılmalıdır.
- Belge kalitesi yetersizse süreç ilerletilmemelidir.
- Belge görüntüleri güvenli şekilde saklanmalı ve sadece yetkili kişiler erişebilmelidir.

### 3.3 Yüz Doğrulama
- Liveness (canlılık) kontrolü yapılmalıdır.
- Yüz eşleştirme skoru belirli bir eşiğin altında kalırsa otomatik onay verilmemelidir.
- Başarısız denemeler sınırlandırılmalı ve sonrasında manuel incelemeye yönlendirilmelidir.

### 3.4 Sonuç ve Karar
- Otomatik onay, manuel inceleme ve red kararları net kurallara bağlanmalıdır.
- Reddedilen kullanıcılara makul bir bilgilendirme yapılmalıdır.
- Manuel inceleme sürecinin azami tamamlanma süresi tanımlanmalıdır.

---

## 4. Veri İşleme ve Saklama Notları

- Kimlik belgesi görüntüleri ve biyometrik veriler sadece doğrulama amacıyla işlenmelidir.
- Saklama süreleri net tanımlanmalı ve süre sonunda silinme / anonimleştirme süreci kurulmalıdır.
- Verilere erişim rol bazlı olmalı ve erişim logları tutulmalıdır.
- Üçüncü taraf servisler (OCR, yüz doğrulama) kullanılıyorsa, veri işleme sözleşmeleri gözden geçirilmelidir.

---

## 5. Risk Azaltma Önerileri

| Risk                              | Öneri                                                      |
|-----------------------------------|------------------------------------------------------------|
| Sahte belge yükleme               | OCR + liveness + manuel inceleme kombinasyonu              |
| Başkasının kimliği ile işlem      | Yüz eşleştirme + liveness zorunluluğu                      |
| Çok sayıda başarısız deneme       | Deneme hakkı sınırı + otomatik manuel inceleme             |
| Veri sızıntısı                    | Şifreleme, erişim kontrolü, loglama                        |
| Kullanıcıya yetersiz bilgilendirme| Her kritik adımda açık ve anlaşılır metinler               |

---

## 6. Compliance ile İş Birliği Noktaları

Business Analyst olarak Compliance ekibi ile şu konularda mutlaka hizalanılmalıdır:

- Hangi belge türlerinin kabul edileceği
- Otomatik onay / manuel inceleme / red kuralları
- Saklama süreleri ve silme politikaları
- Üçüncü taraf servislerin kullanım şartları
- Kullanıcıya gösterilecek yasal bilgilendirme metinleri

---

## 7. Notlar

- Bu doküman genel bir çerçeve sunar. Kesin kurallar ve onaylar Compliance / Hukuk ekibi tarafından verilmelidir.
- Süreç tasarlanırken “güvenlik ve uyumluluk” ile “kullanıcı deneyimi” dengesi gözetilmelidir.
- Tüm kritik karar noktaları dokümante edilmeli ve denetimlere hazır tutulmalıdır.
