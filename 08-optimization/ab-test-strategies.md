# A/B Test Stratejileri

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, onboarding süreci ve bildirimlerde yapılacak A/B testlerin kapsamını, önceliklerini ve ölçüm yöntemlerini tanımlar.

---

## 2. A/B Test Prensipleri

- Aynı anda mümkün olduğunca **tek bir değişken** test edilmelidir.
- Test süresi istatistiksel anlamlılık oluşana kadar devam etmelidir (genelde minimum 1-2 hafta).
- Yeterli örneklem büyüklüğü olmadan karar verilmemelidir.
- Kazanan varyant net olduktan sonra tüm kullanıcılara uygulanmalıdır.
- Test sonuçları dokümante edilmelidir.

---

## 3. Öncelikli Test Alanları

| Öncelik | Test Alanı                            | Neden Önemli?                              | Beklenen Etki            |
|---------|---------------------------------------|--------------------------------------------|--------------------------|
| Yüksek  | Push bildirim metinleri               | Hatırlatma bildirimlerinin tıklanma oranı  | Drop-off azaltma         |
| Yüksek  | Hatırlatma zamanlaması                | 1s / 24s / 72s zamanlamasının etkisi       | Tamamlanma oranı         |
| Orta    | OTP ekranı metinleri                  | Doğrulama adımında terk etme               | OTP başarı oranı         |
| Orta    | Belge yükleme yönlendirme metinleri   | OCR başarı oranı ve deneme sayısı          | OCR başarı oranı         |
| Orta    | Sonuç ekranı (Onay / Red) metinleri   | Kullanıcı memnuniyeti ve destek talebi     | Destek talebi oranı      |
| Düşük   | Buton metinleri                       | “Devam Et” vs “Tamamla” gibi mikro metinler| Dönüşüm oranı            |

---

## 4. Bildirimler İçin Örnek A/B Test Senaryoları

### Test 1: 1 Saat Hatırlatma Metni

| Varyant     | Başlık                        | Metin                                                                 | Hipotez |
|-------------|-------------------------------|-----------------------------------------------------------------------|---------|
| A (Mevcut)  | Kimlik doğrulamanız eksik     | Kaldığınız yerden devam ederek hesabınızı hızlıca aktif edebilirsiniz.| - |
| B           | Hesabınızı tamamlayın         | Kimlik doğrulamanızı bitirin, hemen kullanmaya başlayın.              | Daha net aksiyon + fayda vurgusu tıklanmayı artırır |

**Ölçülecek Metrik:** Tıklanma oranı (CTR) + 24 saat içinde onboarding tamamlama oranı

### Test 2: Hatırlatma Zamanlaması

| Varyant | Gönderim Zamanı | Hipotez |
|---------|------------------|---------|
| A       | 1 saat sonra     | Erken hatırlatma daha etkili olur |
| B       | 3 saat sonra     | Kullanıcıya daha fazla nefes alma süresi vermek dönüşümü artırır |

**Ölçülecek Metrik:** Hatırlatma sonrası tamamlanma oranı

### Test 3: Onay Bildirimi Tonu

| Varyant | Başlık               | Metin                                                                 | Hipotez |
|---------|----------------------|-----------------------------------------------------------------------|---------|
| A       | Hesabınız onaylandı  | Tebrikler! Kimlik doğrulamanız tamamlandı. Artık işlem yapabilirsiniz.| - |
| B       | Artık hazırsınız     | Kimlik doğrulamanız tamamlandı. Hesabınızı kullanmaya başlayabilirsiniz. | Daha sade ve sakin ton daha olumlu algılanır |

---

## 5. Başarı Metrikleri (A/B Test İçin)

| Metrik                        | Açıklama                                      |
|-------------------------------|-----------------------------------------------|
| CTR (Click-Through Rate)      | Bildirime tıklayan / Gönderilen bildirim      |
| Completion Rate               | Bildirim sonrası onboarding tamamlama oranı   |
| Time to Complete              | Bildirimden sonra tamamlamaya kadar geçen süre|
| Unsubscribe / Opt-out Rate    | Bildirimlerden çıkan kullanıcı oranı          |
| Support Ticket Rate           | Bildirim sonrası destek talebi oranı          |

---

## 6. Test Süreci (Önerilen)

1. Hipotez belirle
2. Varyantları oluştur
3. Örneklem büyüklüğünü hesapla
4. Testi başlat (eşit trafik dağılımı)
5. Verileri topla
6. İstatistiksel anlamlılığı kontrol et
7. Kazanan varyantı uygula
8. Sonucu dokümante et

---

## 7. Notlar

- Özellikle erken aşamada (ilk 4-6 hafta) bildirim metinleri ve zamanlaması en yüksek etkili test alanlarıdır.
- Testler Product Owner onayı ile planlanmalıdır.
- Çok fazla testi aynı anda çalıştırmak sonuçları kirletebilir.
- Bu doküman ilerleyen süreçte yeni test alanları eklendikçe güncellenecektir.
