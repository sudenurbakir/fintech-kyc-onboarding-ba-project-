# Bildirim Kuralları ve Prensipler

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, push bildirimlerinin ne zaman ve hangi kurallarla gönderileceğini tanımlar. Ana senaryolar `push-notification-scenarios.md` dosyasında yer alır.

---

## 2. Bildirim Tetikleme Kuralları

| Durum                        | Bildirim Gönderilir mi? | Ne Zaman            | Açıklama                                |
|-----------------------------|-------------------------|---------------------|-----------------------------------------|
| Onboarding yarıda bırakıldı | Evet                    | 1 saat sonra        | İlk hatırlatma                          |
| 24 saat geçti               | Evet                    | 24 saat sonra       | İkinci hatırlatma                       |
| 72 saat geçti               | Evet                    | 72 saat sonra       | Son hatırlatma (daha sonra gönderilmez) |
| Manuel incelemeye alındı    | Evet                    | Anında              | Bilgilendirme                           |
| KYC onaylandı               | Evet                    | Anında              | Pozitif sonuç                           |
| KYC reddedildi              | Evet                    | Anında              | Sonuç bildirimi                         |
| OCR / Yüz doğrulama hatası  | Hayır (genelde)         | -                   | Sadece in-app mesaj tercih edilir       |

---

## 3. Gönderim Prensipleri

- Aynı kullanıcıya aynı gün içinde birden fazla hatırlatma gönderilmez.
- Saat 22:00 – 08:00 arasında hatırlatma tipi bildirimler gönderilmez.
- Kritik sonuç bildirimleri (Onay / Red / Manuel İnceleme) her durumda gönderilir.
- Kullanıcı bildirimleri kapatsa bile, uygulama içi (in-app) bilgilendirme gösterilir.
- Bildirim metinleri kısa, net ve eyleme yönlendirici olmalıdır.
- Mümkün olduğunda deep link ile kullanıcı ilgili ekrana yönlendirilir.

---

## 4. Frequency Cap Özeti

| Bildirim Tipi          | Maksimum Gönderim          |
|------------------------|----------------------------|
| Hatırlatma (1s / 24s / 72s) | Toplam 3 adet             |
| Sonuç bildirimleri     | Her durum değişikliğinde 1 |
| Hata bildirimleri      | Genelde gönderilmez        |

---

## 5. Notlar

- Bu kurallar Product Owner ve UX ile birlikte gözden geçirilmelidir.
- Bildirim performans metrikleri (tıklanma, dönüşüm) takip edilerek metinler optimize edilebilir.
