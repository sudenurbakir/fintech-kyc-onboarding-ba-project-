# Risk Kaydı (Risk Register)

**Proje:** Fintech Mobil Uygulama – Kullanıcı Onboarding & KYC Süreci  
**Doküman Sahibi:** Sudenur Bakır - Business Analyst  
**Versiyon:** 1.0

## 1. Amaç
Bu doküman, KYC onboarding sürecinde karşılaşılabilecek başlıca riskleri, etki ve olasılık seviyelerini ve önerilen önlemleri listeler.

---

## 2. Risk Matrisi

| #  | Risk                                      | Olasılık | Etki   | Seviye  | Önlem / Aksiyon                                                                 | Sorumlu          | Durum      |
|----|-------------------------------------------|----------|--------|---------|----------------------------------------------------------------------------------|------------------|------------|
| 1  | Sahte veya manipüle edilmiş belge yükleme | Orta     | Yüksek | Yüksek  | OCR + liveness + skor eşikleri + manuel inceleme kuyruğu                        | Compliance + BA  | Açık       |
| 2  | Başkasının kimliği ile hesap açma         | Orta     | Yüksek | Yüksek  | Yüz eşleştirme zorunluluğu + liveness kontrolü                                  | Compliance + Dev | Açık       |
| 3  | OCR başarı oranının düşük olması          | Orta     | Orta   | Orta    | Kalite kontrolü, kullanıcıya net yönlendirme, 3 deneme hakkı                    | BA + UX + Dev    | Açık       |
| 4  | Yüksek drop-off (yarıda bırakma) oranı    | Yüksek   | Orta   | Yüksek  | Push hatırlatmaları, kaldığı yerden devam, sade akış tasarımı                   | Product + BA     | Açık       |
| 5  | Kamera / galeri izni verilmemesi           | Orta     | Orta   | Orta    | Açıklayıcı izin ekranı + “Ayarlara Git” yönlendirmesi                           | UX + Mobile      | Açık       |
| 6  | OTP rate limit aşımı / spam               | Düşük    | Orta   | Düşük   | Gönderim sıklığı sınırı (rate limit)                                            | Backend          | Açık       |
| 7  | Sunucu / üçüncü taraf servis kesintisi    | Düşük    | Yüksek | Orta    | Timeout yönetimi, kullanıcıya anlaşılır hata mesajı, retry mekanizması          | Backend + BA     | Açık       |
| 8  | Veri güvenliği ihlali                     | Düşük    | Kritik | Yüksek  | Şifreleme, erişim kontrolü, loglama, üçüncü taraf sözleşme kontrolleri          | Security + Comp. | Açık       |
| 9  | Manuel inceleme kuyruğunun tıkanması      | Orta     | Orta   | Orta    | Otomatik karar eşiklerinin optimize edilmesi, inceleme SLA’sı tanımlanması      | Compliance + Ops | Açık       |
| 10 | Kullanıcıya yetersiz bilgilendirme        | Orta     | Düşük  | Düşük   | Her adımda net metinler, hata mesajlarının çözüm odaklı yazılması               | BA + UX          | Açık       |
| 11 | Çok fazla başarısız deneme sonrası kötüye kullanım | Orta | Orta | Orta | Deneme hakkı sınırı + otomatik manuel inceleme veya geçici kısıtlama         | Compliance + Dev | Açık       |
| 12 | Sonuç ekranlarında geri tuşu ile manipülasyon | Düşük | Orta | Düşük | Sonuç ekranlarında geri tuşunun devre dışı bırakılması                          | Mobile           | Açık       |

---

## 3. Risk Seviyesi Açıklaması

| Seviye  | Açıklama                                      | Aksiyon Beklentisi                  |
|---------|-----------------------------------------------|-------------------------------------|
| Kritik  | Projeyi veya kullanıcı güvenliğini ciddi etkiler | Hemen ele alınmalı                  |
| Yüksek  | Önemli etki yaratabilir                       | Öncelikli planlanmalı               |
| Orta    | Yönetilebilir ama ihmal edilmemeli             | İzlenmeli ve önlem alınmalı         |
| Düşük   | Sınırlı etki                                  | İzlenmeli, gerekirse aksiyon alınır |

---

## 4. Risk Yönetim Notları

- Riskler sprint planlamalarında periyodik olarak gözden geçirilmelidir.
- Özellikle **Yüksek** ve **Kritik** seviyedeki riskler için net aksiyon sahibi atanmalıdır.
- Yeni bir edge case veya teknik kısıt ortaya çıktığında risk kaydı güncellenmelidir.
- Compliance ve Security ekipleri ile ortak gözden geçirme yapılmalıdır.

---

## 5. Takip

| Alan              | Sıklık          | Sorumlu             |
|-------------------|-----------------|---------------------|
| Risk gözden geçirme | 2 haftada bir | Business Analyst    |
| Yüksek risk aksiyon takibi | Haftalık     | İlgili Sorumlu      |
| Compliance onayı  | Milestone bazlı | Compliance Officer |

---

## 6. Notlar

- Bu risk kaydı canlı bir dokümandır. Proje ilerledikçe güncellenmelidir.
- Her risk için mümkün olduğunca ölçülebilir önlemler tanımlanmalıdır.
- Risklerin azaltılması, kullanıcı deneyimini gereksiz yere zorlaştırmamalıdır.
