# Sprint 6 + Vize Kontrol Listesi

- [ ] 1. Tüm linkler çalışıyor.
- [ ] 2. Tüm sayfalar hazır.
- [ ] 3. Klasör ve dosya yapısı oluşturuldu.
- [ ] 4. Tüm route'lar (10 adet) tanımlandı.
- [ ] 5. Context kullanıldı ve gerekli tüm sayfalara bağlandı.
- [ ] 6. Ekle, sil, güncelle ve silmeden önce onay çalışıyor; etkisi diğer sayfalarda görülüyor.
- [ ] 7. Son çalışır proje GitHub'a gönderildi.
- [ ] 8. Proje Vercel'de `isimsoyisim-frontend.vercel.app` biçiminde yayında.
- [ ] 9. README yazıldı, Vercel linki README'ye eklendi.
- [ ] 10. Mobil görünüm doğru çalışıyor.
- [ ] 11. CSS bozulması yok.
- [ ] 12. Arama ve filtreleme çalışıyor.
- [ ] 13. Form doğrulama çalışıyor: etkinlik formu, giriş, kayıt, şifremi unuttum.

## Kritik testler

1. `/events/event-2` Robotik Atölyesi'ni açmalı.
2. `/events/yok` → Sayfa bulunamadı.
3. Yönetim → Yeni etkinlik → boş Kaydet: 7 alan hata vermeli.
4. Geçerli yeni etkinlik eklenince `/admin`, `/` ve `/events` listelerinde görünmeli.
5. Düzenle ile değiştirilen etkinlik diğer sayfalarda güncellenmeli.
6. Sil düğmesi önce `window.confirm` sormalı; onay sonrası her listeden silinmeli.
7. Sayfayı yenileyince Context başlangıç verisine dönmeli; bu sprint için normaldir.
8. Login boş gönderim: e-posta + şifre hatası.
9. Register farklı iki şifre: `Şifreler aynı değil.`
10. Forgot password geçerli e-posta: demo gönderim mesajı.
11. `npm run build` hatasız bitmeli.
