# Edge Case & Hata Yönetimi Matrisi

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu matris, onboarding sürecinde karşılaşılabilecek istisnai durumları, kullanıcıya gösterilecek mesajları ve sistem davranışlarını tanımlar.

---

## 2. Edge Case Matrisi

| #  | Senaryo                              | Tetikleyici                          | Kullanıcıya Gösterilecek Mesaj / Ekran                                      | Sistem Davranışı                                      | Öncelik  |
|----|--------------------------------------|--------------------------------------|-----------------------------------------------------------------------------|-------------------------------------------------------|----------|
| 1  | İnternet bağlantısı koptu            | Network offline                      | “İnternet bağlantınız koptu. Lütfen bağlantınızı kontrol edin.” + Tekrar Dene | İşlemi geçici olarak durdurur, bağlantı gelince devam etmeye çalışır | Yüksek   |
| 2  | Kamera izni reddedildi               | Permission denied                    | “Kamera izni gerekli. Kimlik belgenizi tarayabilmek için izne ihtiyacımız var.” + Ayarlara Git | Süreç ilerletilmez, izin alınana kadar bekler        | Yüksek   |
| 3  | OCR başarısız (bulanık / yansıma)    | OCR confidence düşük                 | “Belge net okunamadı. Lütfen daha iyi ışıkta ve düz zeminde tekrar deneyin.” | 3 deneme hakkı verir, 3. denemeden sonra manuel inceleme seçeneği sunar | Yüksek   |
| 4  | Yüz eşleşmesi başarısız              | Face match score düşük               | “Yüzünüz kimlik belgesi ile eşleşmedi. Lütfen tekrar deneyin.”              | Maksimum 3 deneme hakkı verir, sonrasında manuel incelemeye alır | Yüksek   |
| 5  | OTP gelmedi / süre doldu             | Timeout veya kullanıcı talebi        | “Kod gelmedi mi? Tekrar gönder”                                             | Rate limit uygular (örnek: 3 gönderim / 10 dk)       | Orta     |
| 6  | Kullanıcı yarıda bıraktı             | Uygulama kapatıldı / arka plana alındı | Push: “Kimlik doğrulamanız eksik. Kaldığınız yerden devam edebilirsiniz.”  | 1 saat, 24 saat ve 72 saat sonra hatırlatma gönderir (frequency cap ile) | Orta     |
| 7  | Belge kalitesi çok düşük             | Bulanık, karanlık veya kesik belge   | “Belge kalitesi yetersiz. Lütfen daha net bir fotoğraf yükleyin.”           | Kullanıcıyı tekrar çekmeye yönlendirir               | Yüksek   |
| 8  | Belge türü desteklenmiyor            | Yanlış belge yüklendi                | “Bu belge türü desteklenmiyor. Lütfen geçerli bir kimlik belgesi yükleyin.” | Süreci durdurur ve doğru belge ister                 | Yüksek   |
| 9  | Çok fazla başarısız deneme           | 3+ OCR veya yüz doğrulama hatası     | “Birkaç başarısız deneme algılandı. Destek ekibimiz size yardımcı olabilir.” | Manuel inceleme kuyruğuna alır veya destek yönlendirir | Kritik   |
| 10 | Sunucu / servis hatası               | Backend timeout veya servis down     | “Şu an işleminizi gerçekleştiremiyoruz. Lütfen daha sonra tekrar deneyin.”  | Hata loglar, kullanıcıya genel mesaj gösterir        | Yüksek   |

---

## 3. Öncelik Açıklaması

- **Kritik:** Süreci tamamen engelleyebilir, hemen çözülmeli
- **Yüksek:** Kullanıcı deneyimini ciddi bozar, öncelikli ele alınmalı
- **Orta:** Rahatsız edici ama süreci tamamen durdurmaz

---

## 4. Notlar

- Tüm edge case’lerde kullanıcıya **ne olduğu** ve **ne yapması gerektiği** net şekilde söylenmelidir.
- Mümkün olan her durumda kullanıcıya “Tekrar Dene” seçeneği sunulmalıdır.
- Kritik hatalarda (özellikle sahtecilik şüphesi doğurabilecek durumlarda) süreç otomatik olarak manuel incelemeye alınmalıdır.
- Bu matris geliştirme ve test ekipleri ile birlikte gözden geçirilmelidir.
