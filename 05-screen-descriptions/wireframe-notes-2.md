---

## 5. Detaylı Ekran Akışları

### 5.1 Telefon Numarası → OTP Akışı

1. Kullanıcı telefon numarasını girer.
2. “Devam Et” butonuna basar.
3. Sistem numarayı kontrol eder.
   - Geçersizse → Input altında hata mesajı gösterilir, ekranda kalınır.
   - Geçerliyse → OTP ekranına geçilir ve SMS gönderilir.
4. OTP ekranında:
   - Kullanıcı kodu girer.
   - Süre dolarsa → “Tekrar Gönder” aktif olur.
   - Yanlış kod girerse → Hata mesajı + kalan deneme hakkı gösterilir.
   - Doğru kod girerse → Kimlik Belgesi Yükleme ekranına geçilir.

### 5.2 Kimlik Belgesi Yükleme → OCR Akışı

1. Kullanıcı “Kamera ile Çek” veya “Galeriden Seç” seçeneğini seçer.
2. Kamera izni kontrol edilir.
   - İzin yoksa → İzin bilgilendirme ekranı gösterilir.
   - İzin varsa → Kamera/galeri açılır.
3. Belge seçilir/çekilir → Önizleme ekranı açılır.
4. Kullanıcı “Kullan” derse → OCR loading ekranı gösterilir.
5. OCR sonucu:
   - Başarılıysa → Bilgi Onay ekranına geçilir.
   - Başarısızsa → Hata mesajı + “Tekrar Dene” seçeneği gösterilir.
6. 3 başarısız denemeden sonra → “Manuel İnceleme Talep Et” seçeneği sunulur.

### 5.3 Yüz Doğrulama Akışı

1. Kullanıcı Bilgi Onay ekranından “Devam Et” der.
2. Yüz Doğrulama ekranı açılır.
3. Kullanıcı yüzünü çerçeve içine alır.
4. Liveness + eşleştirme yapılır.
   - Başarılıysa → Sonuç ekranı (Onaylandı) gösterilir.
   - Başarısızsa → Hata mesajı + “Tekrar Dene” gösterilir.
5. 3 başarısız denemeden sonra → Otomatik olarak Manuel İnceleme sonucuna yönlendirilir.

### 5.4 Sonuç Ekranları Akışı

| Durum              | Gösterilecek Ekran       | Sonraki Aksiyon                  |
|--------------------|---------------------------|----------------------------------|
| Onaylandı          | Başarı ekranı             | Ana Sayfaya yönlendirme          |
| Manuel İnceleme    | Bilgilendirme ekranı      | Uygulama içinde bekleme / çıkış  |
| Reddedildi         | Red ekranı                | Destek Al veya Tekrar Dene       |

### 5.5 Geri Tuşu Davranışları

| Ekran                        | Geri Tuşu Davranışı                          |
|-----------------------------|----------------------------------------------|
| Telefon Numarası            | Karşılama ekranına döner                     |
| OTP                         | Telefon numarası ekranına döner              |
| Kimlik Belgesi Yükleme      | OTP ekranına döner                           |
| Belge Önizleme              | Kimlik Belgesi Yükleme ekranına döner        |
| OCR Loading                 | Geri tuşu devre dışı                         |
| Bilgi Onay                  | Belge Önizleme veya Yükleme ekranına döner   |
| Yüz Doğrulama               | Bilgi Onay ekranına döner                    |
| Sonuç Ekranları (hepsi)     | Geri tuşu devre dışı (süreç tamamlandı)      |

---

## 6. Ekran Geçiş Özeti (Happy Path)

```text
Karşılama 
→ Telefon Numarası 
→ OTP Doğrulama 
→ Kimlik Belgesi Yükleme 
→ Belge Önizleme 
→ OCR Loading 
→ Bilgi Onay 
→ Yüz Doğrulama 
→ Sonuç (Onaylandı) 
→ Ana Sayfa
