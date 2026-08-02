# Push Notification Senaryoları

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, onboarding sürecinde kullanıcı davranışına ve sistem durumuna göre gönderilecek push bildirimlerini tanımlar. Bildirimler hem bilgilendirme hem de süreci tamamlatma amacı taşır.

---

## 2. Push Notification Senaryoları

| #  | Tetikleyici                              | Bildirim Başlığı                  | Bildirim Metni                                                                 | Gönderim Zamanı       | Frequency Cap          | Öncelik |
|----|------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------|-----------------------|------------------------|---------|
| 1  | Kullanıcı onboarding’i yarıda bıraktı    | Kimlik doğrulamanız eksik         | Kaldığınız yerden devam ederek hesabınızı hızlıca aktif edebilirsiniz.         | 1 saat sonra          | 1 kez / 24 saat        | Yüksek  |
| 2  | 24 saat geçti, hâlâ tamamlanmadı         | Hâlâ eksik adımınız var           | Kimlik doğrulamanızı tamamlayın, hesabınızı kullanmaya başlayın.               | 24 saat sonra         | Maksimum 2 hatırlatma  | Orta    |
| 3  | 72 saat geçti, hâlâ tamamlanmadı         | Son hatırlatma                    | Kimlik doğrulamanız henüz tamamlanmadı. Şimdi tamamlayabilirsiniz.             | 72 saat sonra         | 1 kez                  | Düşük   |
| 4  | Manuel incelemeye alındı                 | Belgeleriniz inceleniyor          | Kimlik belgeleriniz inceleniyor. En kısa sürede bilgilendireceğiz.             | Anında                | -                      | Yüksek  |
| 5  | KYC onaylandı                            | Hesabınız onaylandı               | Tebrikler! Kimlik doğrulamanız tamamlandı. Artık işlem yapabilirsiniz.         | Anında                | -                      | Yüksek  |
| 6  | KYC reddedildi                           | Doğrulama tamamlanamadı           | Kimlik doğrulamanız tamamlanamadı. Detaylar için uygulamayı açabilirsiniz.     | Anında                | -                      | Yüksek  |
| 7  | OCR veya yüz doğrulama 2. kez başarısız  | Tekrar denemek ister misiniz?     | Belge veya yüz doğrulama başarısız oldu. Tekrar deneyerek devam edebilirsiniz. | Anında (uygulama açık değilse) | 1 kez               | Orta    |

---

## 3. Bildirim Kuralları

- Kullanıcı bildirimleri kapatmış olsa bile, kritik sonuçlar (Onay / Red) in-app olarak da gösterilmelidir.
- Aynı kullanıcıya aynı günde birden fazla hatırlatma gönderilmemelidir (frequency cap).
- Bildirim metinleri kısa, net ve eyleme yönlendirici olmalıdır.
- Kullanıcı uygulamayı açtığında, ilgili durum için in-app mesaj da gösterilmelidir.
- Saat 22:00 – 08:00 arasında hatırlatma tipi bildirimler gönderilmemelidir (sessiz saat uygulaması).

---

## 4. Bildirim Öncelik Açıklaması

| Öncelik | Açıklama                                      | Örnek                          |
|---------|-----------------------------------------------|--------------------------------|
| Yüksek  | Kullanıcının hemen bilmesi gereken durumlar   | Onay, Red, Manuel İnceleme     |
| Orta    | Süreci tamamlamaya teşvik eden hatırlatmalar  | 24 saat hatırlatma             |
| Düşük   | Son çaba niteliğindeki hatırlatmalar          | 72 saat son hatırlatma         |

---

## 5. Notlar

- Tüm bildirim metinleri UX ve ürün ekibi ile birlikte son haline getirilmelidir.
- Bildirimlerin tıklanma ve dönüşüm oranları ölçülerek metinler optimize edilebilir.
- Bu senaryolar edge case matrisi ile uyumlu çalışmalıdır.
