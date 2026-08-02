## 7. Hata Durumları (Error States)

### 7.1 Telefon Numarası Ekranı

| Hata                    | Kullanıcıya Gösterilecek Mesaj                          | Davranış                              |
|-------------------------|---------------------------------------------------------|---------------------------------------|
| Geçersiz format         | “Geçerli bir telefon numarası giriniz”                  | Input kırmızı olur, buton pasif kalır |
| Boş bırakma             | “Telefon numarası zorunludur”                           | Buton pasif kalır                     |
| Daha önce kayıtlı numara| “Bu numara ile zaten bir hesap bulunuyor”               | Giriş yapmaya yönlendirme seçeneği sunulabilir |

### 7.2 OTP Doğrulama Ekranı

| Hata                    | Kullanıcıya Gösterilecek Mesaj                          | Davranış                              |
|-------------------------|---------------------------------------------------------|---------------------------------------|
| Yanlış kod              | “Kod hatalı, kalan deneme hakkı: X”                     | Input temizlenir, deneme hakkı azalır |
| 3 yanlış deneme         | “Çok fazla hatalı deneme yaptınız. Lütfen daha sonra tekrar deneyin.” | Ekran kilitlenir, belirli süre sonra tekrar denenebilir |
| Süre doldu              | “Kodun süresi doldu”                                    | “Tekrar Gönder” butonu aktif olur     |
| Rate limit aşıldı       | “Çok fazla kod talebinde bulundunuz. Lütfen 10 dakika sonra tekrar deneyin.” | Tekrar Gönder butonu pasif kalır |

### 7.3 Kimlik Belgesi Yükleme Ekranı

| Hata                    | Kullanıcıya Gösterilecek Mesaj                          | Davranış                              |
|-------------------------|---------------------------------------------------------|---------------------------------------|
| Kamera izni yok         | “Kamera izni gerekli. Kimlik belgenizi tarayabilmek için izne ihtiyacımız var.” | “Ayarlara Git” butonu gösterilir      |
| Galeri izni yok         | “Galeri erişimi gerekli”                                | “Ayarlara Git” butonu gösterilir      |
| Belge seçilmedi / iptal | -                                                       | Aynı ekranda kalınır                  |

### 7.4 Belge Önizleme & OCR

| Hata                    | Kullanıcıya Gösterilecek Mesaj                          | Davranış                              |
|-------------------------|---------------------------------------------------------|---------------------------------------|
| Belge çok bulanık       | “Belge net değil. Lütfen daha iyi ışıkta tekrar çekin.” | “Tekrar Çek” seçeneği sunulur         |
| Belge kesik / açı bozuk | “Belgenin tamamı görünmüyor. Lütfen yeniden konumlandırın.” | “Tekrar Çek” seçeneği sunulur         |
| OCR başarısız           | “Belge okunamadı. Lütfen tekrar deneyin.”               | 3 deneme hakkı, sonra Manuel İnceleme seçeneği |
| OCR timeout             | “İşlem zaman aşımına uğradı. Lütfen tekrar deneyin.”    | “Tekrar Dene” butonu gösterilir       |
| Desteklenmeyen belge    | “Bu belge türü desteklenmiyor. Lütfen geçerli bir kimlik belgesi yükleyin.” | Süreci başa döndürme seçeneği         |

### 7.5 Yüz Doğrulama Ekranı

| Hata                    | Kullanıcıya Gösterilecek Mesaj                          | Davranış                              |
|-------------------------|---------------------------------------------------------|---------------------------------------|
| Yüz algılanamadı        | “Yüzünüz algılanamadı. Lütfen daha iyi aydınlatılmış bir ortamda deneyin.” | Tekrar deneme yönlendirmesi           |
| Liveness başarısız      | “Canlılık kontrolü başarısız. Lütfen hareketleri tekrar yapın.” | Tekrar deneme                         |
| Yüz eşleşmedi           | “Yüzünüz kimlik belgesi ile eşleşmedi. Lütfen tekrar deneyin.” | Maksimum 3 deneme, sonra Manuel İnceleme |
| 3 başarısız deneme      | “Doğrulama tamamlanamadı. Belgeleriniz incelemeye alındı.” | Otomatik Manuel İnceleme sonucuna geçiş |

### 7.6 Genel / Sistem Hataları

| Hata                    | Kullanıcıya Gösterilecek Mesaj                          | Davranış                              |
|-------------------------|---------------------------------------------------------|---------------------------------------|
| İnternet yok            | “İnternet bağlantınız koptu. Lütfen bağlantınızı kontrol edin.” | “Tekrar Dene” butonu                  |
| Sunucu hatası           | “Şu an işleminizi gerçekleştiremiyoruz. Lütfen daha sonra tekrar deneyin.” | “Tekrar Dene” + destek yönlendirmesi  |
| Beklenmeyen hata        | “Bir şeyler ters gitti. Lütfen tekrar deneyin.”         | “Tekrar Dene” butonu                  |

---

## 8. Hata Durumu Tasarım Prensipleri

- Her hatada kullanıcıya **ne olduğu** ve **ne yapması gerektiği** net söylenmelidir.
- Mümkün olan her durumda “Tekrar Dene” seçeneği sunulmalıdır.
- Kritik hatalarda (3+ başarısız deneme vb.) kullanıcıyı Manuel İnceleme veya Destek’e yönlendirmek tercih edilmelidir.
- Hata mesajları suçlayıcı olmamalı, çözüm odaklı olmalıdır.
- Aynı hata art arda tekrarlanıyorsa, deneme hakkı ve sonraki adım net gösterilmelidir.
