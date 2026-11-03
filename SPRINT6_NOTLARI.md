# Sprint 6'da ne değişti?

- Sprint 5'teki state tabanlı sayfa geçişi kaldırıldı; React Router geldi.
- `types/page.ts`, `PageName`, App'teki `page` state'i ve `go()` kaldırıldı.
- 10 route gerçek URL'lerle tanımlandı.
- `Navigation` artık `NavLink`, kart ve detay bağlantıları `Link` kullanıyor.
- `EventDetailPage` URL'deki `:id` değerini `useParams()` ile okuyor.
- Etkinlik listesi ve CRUD fonksiyonları `EventsContext` içinde tutuluyor.
- HomePage, EventsPage, EventDetailPage ve Admin sayfaları `useEvents()` ile Context'e erişiyor.
- EventForm controlled form oldu; tüm değerler tek `data` state nesnesinde tutuluyor.
- `validateEvent` 7 alanı doğruluyor ve hata nesnesi döndürüyor.
- Ekle / Güncelle aynı EventForm'u farklı `initialData` ile kullanıyor.
- Admin sayfasında masaüstünde tablo, telefonda kart görünümü var.
- Login / Register / ForgotPassword sayfaları controlled input ve doğrulama içeriyor; backend yok.
