# Alternative Flows – Alternatif Akışlar

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, Happy Path dışındaki olası alternatif akışları tanımlar. Kullanıcı veya sistem kaynaklı sapmaların nasıl yönetileceğini gösterir.

---

## 2. Alternatif Akış Listesi

### AF-01: OTP Gelmedi / Süre Doldu

**Tetikleyici:** Kullanıcı OTP’yi zamanında alamadı veya süre doldu.

**Akış:**
1. Kullanıcı “Kod gelmedi mi?” veya süre dolumu mesajını görür.
2. “Tekrar Gönder” butonu aktif olur (60 saniye bekleme sonrası).
3. Sistem yeni OTP gönderir.
4. Rate limit kontrolü yapılır (10 dakika içinde maksimum 3 gönderim).
5. Kullanıcı yeni kodu girer ve sürece devam eder.

**Sonuç:** Happy Path’e geri dönülür.

---

### AF-02: OCR Başarısız (Belge Okunamadı)

**Tetikleyici:** OCR motoru belgeyi okuyamaz (bulanıklık, yansıma, yanlış açı vb.).

**Akış:**
1. Kullanıcıya “Belge net okunamadı” mesajı gösterilir.
2. “Tekrar Dene” butonu sunulur.
3. Kullanıcı belgeyi yeniden çeker/yükler.
4. 3 başarısız denemeden sonra “Manuel İnceleme Talep Et” seçeneği çıkar.
5. Kullanıcı manuel incelemeyi seçerse süreç Manuel İnceleme akışına geçer.

**Sonuç:** Ya Happy Path’e döner ya da Manuel İnceleme’ye gider.

---

### AF-03: Yüz Doğrulama Başarısız

**Tetikleyici:** Yüz eşleşmesi veya liveness kontrolü başarısız olur.

**Akış:**
1. Kullanıcıya “Yüzünüz kimlik belgesi ile eşleşmedi” mesajı gösterilir.
2. “Tekrar Dene” butonu sunulur.
3. Kullanıcı yeniden selfie çeker.
4. Maksimum 3 deneme hakkı verilir.
5. 3. denemeden sonra otomatik olarak Manuel İnceleme kuyruğuna alınır.

**Sonuç:** Ya başarılı olur ve onaylanır, ya da Manuel İnceleme’ye düşer.

---

### AF-04: Kullanıcı Yarıda Bıraktı (Abandonment)

**Tetikleyici:** Kullanıcı uygulamayı kapattı veya arka plana aldı ve geri dönmedi.

**Akış:**
1. Sistem yarıda kalan süreci kaydeder.
2. Belirli süre sonra (örnek: 1 saat) hatırlatma push bildirimi gönderilir.
3. Kullanıcı uygulamayı tekrar açtığında kaldığı adımdan devam etme seçeneği sunulur.
4. 24 saat ve 72 saat sonra ek hatırlatmalar yapılabilir (frequency cap ile).

**Sonuç:** Kullanıcı geri dönerse kaldığı yerden devam eder.

---

### AF-05: Kamera İzni Reddedildi

**Tetikleyici:** Kullanıcı kamera iznini vermedi.

**Akış:**
1. Sistem özel bir bilgilendirme ekranı gösterir.
2. “Kamera izni gerekli” açıklaması yapılır.
3. “Ayarlara Git” butonu sunulur.
4. Kullanıcı izin verene kadar süreç ilerletilmez.
5. İzin verildikten sonra belge yükleme adımına geri dönülür.

**Sonuç:** İzin alındıktan sonra Happy Path’e devam edilir.

---

### AF-06: İnternet Bağlantısı Koptu

**Tetikleyici:** İşlem sırasında internet bağlantısı kesilir.

**Akış:**
1. Kullanıcıya “İnternet bağlantınız koptu” mesajı gösterilir.
2. “Tekrar Dene” butonu çıkar.
3. Bağlantı geri geldiğinde sistem işlemi kaldığı yerden devam ettirmeye çalışır.
4. Kritik adımlarda (OTP, OCR, Yüz Doğrulama) işlem yeniden başlatılabilir.

**Sonuç:** Bağlantı sağlandıktan sonra sürece devam edilir.

---

## 3. Notlar

- Tüm alternatif akışlar edge case matrisi ile birlikte değerlendirilmelidir.
- Her alternatif akışın sonunda kullanıcıya net bir sonraki adım gösterilmelidir.
- Alternatif akışlar mümkün olduğunca Happy Path’e geri döndürmeye çalışmalıdır.
