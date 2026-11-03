# Sprint 6 + Vize — Tüm Kodlar

Sprint 5 üzerine uygulanan Sprint 6 kodları.

## `frontend/package.json`

```json
{
  "name": "kampus-etkinlikleri-frontend",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc -b && vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^19.1.1",
    "react-dom": "^19.1.1",
    "react-router-dom": "^7.18.5"
  },
  "devDependencies": {
    "@eslint/js": "^9.36.0",
    "@types/node": "^24.5.2",
    "@types/react": "^19.1.16",
    "@types/react-dom": "^19.1.9",
    "@vitejs/plugin-react": "^5.0.4",
    "eslint": "^9.36.0",
    "eslint-plugin-react-hooks": "^5.2.0",
    "eslint-plugin-react-refresh": "^0.4.22",
    "globals": "^16.4.0",
    "typescript": "~5.9.3",
    "typescript-eslint": "^8.45.0",
    "vite": "^7.1.7"
  }
}

```

## `frontend/vercel.json`

```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}

```

## `frontend/src/main.tsx`

```tsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import { BrowserRouter } from "react-router-dom";
import "./index.css";
import App from "./App";
import { EventsProvider } from "./context/EventsContext";

createRoot(document.getElementById("root")!).render(
  <StrictMode>
    <BrowserRouter>
      <EventsProvider>
        <App />
      </EventsProvider>
    </BrowserRouter>
  </StrictMode>,
);

```

## `frontend/src/App.tsx`

```tsx
import { Route, Routes } from "react-router-dom";
import "./App.css";
import Header from "./components/layout/Header";
import Navigation from "./components/layout/Navigation";
import Footer from "./components/layout/Footer";
import HomePage from "./pages/HomePage";
import EventsPage from "./pages/EventsPage";
import EventDetailPage from "./pages/EventDetailPage";
import LoginPage from "./pages/LoginPage";
import RegisterPage from "./pages/RegisterPage";
import ForgotPasswordPage from "./pages/ForgotPasswordPage";
import AdminPage from "./pages/AdminPage";
import AddEventPage from "./pages/AddEventPage";
import EditEventPage from "./pages/EditEventPage";
import NotFoundPage from "./pages/NotFoundPage";

function App() {
  return (
    <>
      <header className="site-header">
        <div className="header-icerik">
          <Header />
          <Navigation />
        </div>
      </header>

      <main>
        <Routes>
          <Route path="/" element={<HomePage />} />
          <Route path="/events" element={<EventsPage />} />
          <Route path="/events/:id" element={<EventDetailPage />} />
          <Route path="/login" element={<LoginPage />} />
          <Route path="/register" element={<RegisterPage />} />
          <Route path="/forgot-password" element={<ForgotPasswordPage />} />
          <Route path="/admin" element={<AdminPage />} />
          <Route path="/admin/new" element={<AddEventPage />} />
          <Route path="/admin/:id/edit" element={<EditEventPage />} />
          <Route path="*" element={<NotFoundPage />} />
        </Routes>
      </main>

      <Footer />
    </>
  );
}

export default App;

```

## `frontend/src/App.css`

```css
:root {
  --ana-renk: #159447;
  --ana-koyu: #0d6f34;
  --zemin: #f4f8f5;
  --kart: #ffffff;
  --metin: #1d2b22;
  --soluk: #5e6f64;
  --kenar: #d7e3da;
  --hata: #b42318;
  --hata-zemin: #fff1f0;
  --basari: #16794b;
  --basari-zemin: #effaf3;
  --golge: 0 8px 20px rgba(20, 70, 40, 0.08);
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
  color: var(--metin);
  background: var(--zemin);
  line-height: 1.55;
}

.site-header {
  background: var(--ana-renk);
  color: #fff;
  padding: 1.4rem 1rem 1rem;
}

.header-icerik,
main,
.footer-icerik {
  width: min(1100px, calc(100% - 2rem));
  margin-inline: auto;
}

.site-header h1 {
  margin: 0 0 0.75rem;
  font-size: clamp(1.6rem, 4vw, 2.4rem);
}

.site-nav {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.site-nav a {
  color: #fff;
  text-decoration: none;
  padding: 0.45rem 0.75rem;
  border-radius: 0.4rem;
}

.site-nav a:hover,
.site-nav a[aria-current="page"] {
  background: #fff;
  color: var(--ana-koyu);
}

main {
  min-height: 62vh;
  padding: 2rem 0 3rem;
}

.intro {
  margin-bottom: 1.5rem;
}

.intro h2,
.sayfa-baslik {
  margin-top: 0;
}

.etkinlik-listesi {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1rem;
}

.kart,
.kunye-karti,
.form-karti,
.detay-karti,
.filtre {
  background: var(--kart);
  border: 1px solid var(--kenar);
  border-radius: 0.8rem;
  box-shadow: var(--golge);
}

.kart {
  padding: 1.1rem;
  border-top: 4px solid var(--ana-renk);
}

.kart h2 {
  margin: 0 0 0.25rem;
  font-size: 1.2rem;
}

.kategori-etiketi {
  display: inline-block;
  margin: 0 0 0.8rem;
  color: var(--ana-koyu);
  font-weight: 700;
}

.kart-kunye,
.kunye-karti dl {
  margin: 0;
}

.kart-kunye div,
.kunye-karti dl div {
  display: grid;
  grid-template-columns: 90px 1fr;
  gap: 0.5rem;
  padding: 0.25rem 0;
}

.kart-kunye dt,
.kunye-karti dt {
  font-weight: 700;
}

.kart-kunye dd,
.kunye-karti dd {
  margin: 0;
}

.buton {
  display: inline-block;
  border: 0;
  border-radius: 0.45rem;
  padding: 0.65rem 0.9rem;
  background: var(--ana-renk);
  color: #fff;
  text-decoration: none;
  font: inherit;
  cursor: pointer;
}

.buton:hover {
  background: var(--ana-koyu);
}

.buton.ikincil {
  background: #fff;
  color: var(--ana-koyu);
  border: 1px solid var(--ana-renk);
}

.filtre {
  display: grid;
  grid-template-columns: 1fr 220px;
  gap: 0.8rem 1rem;
  padding: 1rem;
  margin-bottom: 0.5rem;
}

.filtre .alan-grubu {
  display: grid;
  gap: 0.35rem;
}

.filtre label,
.form-karti label {
  font-weight: 700;
}

input,
select,
textarea {
  width: 100%;
  border: 1px solid #aebdb3;
  border-radius: 0.4rem;
  padding: 0.7rem;
  font: inherit;
  background: #fff;
  color: var(--metin);
}

input:focus,
select:focus,
textarea:focus {
  outline: 3px solid rgba(21, 148, 71, 0.18);
  border-color: var(--ana-renk);
}

#sonuc {
  margin: 0.6rem 0 1.2rem;
  color: var(--ana-koyu);
  font-weight: 700;
}

.bos-sonuc {
  grid-column: 1 / -1;
  background: #fff;
  border: 1px dashed var(--kenar);
  padding: 1rem;
  border-radius: 0.6rem;
}

.detay-karti {
  padding: 1rem;
  display: grid;
  grid-template-columns: minmax(230px, 0.8fr) minmax(300px, 1.2fr);
  gap: 1.2rem;
  align-items: start;
}

.detay-karti.detay-afissiz {
  grid-template-columns: 1fr;
}

.afis-figure {
  margin: 0;
}

.afis-gorsel {
  display: block;
  width: 100%;
  max-height: 420px;
  object-fit: cover;
  border: 4px solid #2f4a68;
  outline: 2px solid #d39b7f;
  background: #10233c;
}

.afis-figure figcaption {
  margin-top: 0.55rem;
  color: var(--soluk);
  font-size: 0.9rem;
}

.detay-icerik h1 {
  margin-top: 0;
}

.kunye-karti {
  padding: 1rem;
}

.kunye-karti h2,
.aciklama h2 {
  margin-top: 0;
}

.aciklama {
  margin-top: 1.2rem;
}

.detay-butonlari {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-top: 1rem;
}

.form-aciklama {
  max-width: 760px;
}

.form-karti {
  padding: 1.2rem;
  max-width: 760px;
}

.form-alan {
  display: grid;
  gap: 0.35rem;
  margin-bottom: 1rem;
}

.mesaj {
  max-width: 760px;
  margin-top: 1rem;
  padding: 1rem;
  border-radius: 0.6rem;
}

.hata-kutusu {
  background: var(--hata-zemin);
  color: #7a1c14;
  border: 1px solid #e08f87;
}

.site-footer {
  border-top: 1px solid var(--kenar);
  padding: 1.5rem 0;
  color: var(--soluk);
  text-align: center;
}

@media (max-width: 850px) {
  .etkinlik-listesi {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .detay-karti {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 620px) {
  .header-icerik,
  main,
  .footer-icerik {
    width: min(100% - 1rem, 1100px);
  }

  .etkinlik-listesi,
  .filtre {
    grid-template-columns: 1fr;
  }

  .site-nav {
    gap: 0.3rem;
  }

  .site-nav a {
    padding: 0.4rem 0.55rem;
    font-size: 0.95rem;
  }

  .detay-karti {
    padding: 0.7rem;
  }

  .afis-gorsel {
    max-height: 360px;
  }
}

/* Sprint 6: Router, Context, yönetim ve form doğrulama */
:root {
  --renk-ana: var(--ana-renk);
  --renk-hata: #d63838;
  --bosluk-s: 0.55rem;
  --kose: 0.55rem;
}

.sayfa-aksiyon {
  margin-top: 1.2rem;
}

.hata-metni {
  color: var(--renk-hata);
  font-size: 0.9rem;
}

input[aria-invalid="true"],
select[aria-invalid="true"],
textarea[aria-invalid="true"] {
  border-color: var(--renk-hata);
  background: #fff7f7;
}

.basari-kutusu {
  background: var(--basari-zemin);
  color: var(--basari);
  border: 1px solid #93c9a8;
}

.tablo {
  width: 100%;
  border-collapse: collapse;
  background: var(--kart);
  border: 1px solid var(--kenar);
}

.tablo th,
.tablo td {
  border: 1px solid var(--kenar);
  padding: 0.75rem;
  text-align: left;
  vertical-align: middle;
}

.tablo th {
  background: var(--renk-ana);
  color: #fff;
}

.islemler {
  display: flex;
  gap: var(--bosluk-s);
  flex-wrap: wrap;
}

.buton-sil {
  background: var(--renk-hata);
}

.buton-sil:hover {
  background: #a92727;
}

.auth-kart,
.bulunamadi {
  max-width: 620px;
}

.auth-kart form {
  max-width: 520px;
}

.auth-buton {
  margin-top: 0.25rem;
}

.auth-linkler {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-top: 1rem;
}

.auth-linkler a {
  color: var(--ana-koyu);
}

@media (max-width: 690px) {
  .tablo thead {
    display: none;
  }

  .tablo,
  .tablo tbody,
  .tablo tr,
  .tablo td {
    display: block;
    width: 100%;
  }

  .tablo {
    border: 0;
    background: transparent;
  }

  .tablo tr {
    margin-bottom: 0.8rem;
    border: 1px solid var(--kenar);
    border-radius: var(--kose);
    background: var(--kart);
    padding: 0.7rem;
  }

  .tablo td {
    border: 0;
    padding: 0.3rem 0;
  }

  .tablo td[data-baslik]::before {
    content: attr(data-baslik) ": ";
    font-weight: 700;
  }

  .tablo td.islemler {
    display: flex;
    gap: var(--bosluk-s);
    padding-top: 0.65rem;
  }
}

```

## `frontend/src/components/layout/Header.tsx`

```tsx
function Header() {
  return (
    <div className="site-baslik">
      <h1>Kampüs Etkinlikleri</h1>
      <p>Fakültedeki seminer, atölye ve söyleşileri tek yerden takip edin.</p>
    </div>
  );
}

export default Header;

```

## `frontend/src/components/layout/Navigation.tsx`

```tsx
import { NavLink } from "react-router-dom";

const menu = [
  { to: "/", label: "Ana Sayfa" },
  { to: "/events", label: "Etkinlikler" },
  { to: "/admin", label: "Yönetim" },
  { to: "/login", label: "Giriş" },
];

function Navigation() {
  return (
    <nav className="site-nav" aria-label="Ana menü">
      {menu.map((item) => (
        <NavLink
          key={item.to}
          to={item.to}
          end={item.to === "/"}
        >
          {item.label}
        </NavLink>
      ))}
    </nav>
  );
}

export default Navigation;

```

## `frontend/src/components/layout/Footer.tsx`

```tsx
function Footer() {
  return (
    <footer className="site-footer">
      <div className="footer-icerik">
        2416501075 - Elif Nur Özek - 2026
      </div>
    </footer>
  );
}

export default Footer;

```

## `frontend/src/components/events/EventCard.tsx`

```tsx
import { Link } from "react-router-dom";
import type { CampusEvent } from "../../types/campus-event";
import { formatDate } from "../../utils/format-date";

interface EventCardProps {
  event: CampusEvent;
}

function EventCard({ event }: EventCardProps) {
  return (
    <article className="kart">
      <h2>{event.title}</h2>
      <p className="kategori-etiketi">{event.category}</p>

      <dl className="kart-kunye">
        <div>
          <dt>Tarih</dt>
          <dd>{formatDate(event.date)}</dd>
        </div>
        <div>
          <dt>Saat</dt>
          <dd>{event.time}</dd>
        </div>
        <div>
          <dt>Yer</dt>
          <dd>{event.location}</dd>
        </div>
        <div>
          <dt>Kontenjan</dt>
          <dd>{event.capacity}</dd>
        </div>
      </dl>

      <p>{event.description}</p>
      <Link className="buton" to={`/events/${event.id}`}>
        Detayları gör
      </Link>
    </article>
  );
}

export default EventCard;

```

## `frontend/src/components/events/EventList.tsx`

```tsx
import type { CampusEvent } from "../../types/campus-event";
import EventCard from "./EventCard";

interface EventListProps {
  events: CampusEvent[];
  emptyText?: string;
}

function EventList({ events, emptyText }: EventListProps) {
  if (events.length === 0) {
    return (
      <p className="bos-sonuc">
        {emptyText ?? "Gösterilecek etkinlik bulunamadı."}
      </p>
    );
  }

  return (
    <section className="etkinlik-listesi">
      {events.map((event) => (
        <EventCard key={event.id} event={event} />
      ))}
    </section>
  );
}

export default EventList;

```

## `frontend/src/components/events/EventFilter.tsx`

```tsx
import type { Category } from "../../types/campus-event";

interface EventFilterProps {
  searchText: string;
  category: Category | "";
  categories: Category[];
  onSearchChange: (text: string) => void;
  onCategoryChange: (category: Category | "") => void;
}

function EventFilter({
  searchText,
  category,
  categories,
  onSearchChange,
  onCategoryChange,
}: EventFilterProps) {
  return (
    <form className="filtre" onSubmit={(event) => event.preventDefault()}>
      <div className="alan-grubu">
        <label htmlFor="arama">Etkinlik ara</label>
        <input
          type="search"
          id="arama"
          placeholder="atölye, kariyer, yapay..."
          value={searchText}
          onChange={(event) => onSearchChange(event.target.value)}
        />
      </div>

      <div className="alan-grubu">
        <label htmlFor="kategori-filtre">Kategori</label>
        <select
          id="kategori-filtre"
          value={category}
          onChange={(event) =>
            onCategoryChange(event.target.value as Category | "")
          }
        >
          <option value="">Tümü</option>
          {categories.map((item) => (
            <option key={item} value={item}>
              {item}
            </option>
          ))}
        </select>
      </div>
    </form>
  );
}

export default EventFilter;

```

## `frontend/src/components/events/EventDetail.tsx`

```tsx
import { Link } from "react-router-dom";
import type { CampusEvent } from "../../types/campus-event";
import { formatDate } from "../../utils/format-date";

interface EventDetailProps {
  event: CampusEvent;
}

function EventDetail({ event }: EventDetailProps) {
  return (
    <article className={`detay-karti${event.image ? "" : " detay-afissiz"}`}>
      {event.image && (
        <figure className="afis-figure">
          <img
            className="afis-gorsel"
            src={event.image}
            alt={`${event.title} afişi`}
          />
          <figcaption>{event.title} afişi</figcaption>
        </figure>
      )}

      <div className="detay-icerik">
        <section className="kunye-karti">
          <h2>Etkinlik Künyesi</h2>
          <dl>
            <div>
              <dt>Tarih</dt>
              <dd>{formatDate(event.date)}</dd>
            </div>
            <div>
              <dt>Saat</dt>
              <dd>{event.time}</dd>
            </div>
            <div>
              <dt>Yer</dt>
              <dd>{event.location}</dd>
            </div>
            <div>
              <dt>Kategori</dt>
              <dd>{event.category}</dd>
            </div>
            <div>
              <dt>Kontenjan</dt>
              <dd>{event.capacity} kişi</dd>
            </div>
          </dl>
        </section>

        <section className="aciklama">
          <h2>Açıklama</h2>
          <p>{event.description}</p>
        </section>

        <div className="detay-butonlari">
          <Link className="buton ikincil" to="/events">
            ← Listeye dön
          </Link>
          <Link className="buton" to={`/admin/${event.id}/edit`}>
            Bu etkinliği güncelle
          </Link>
        </div>
      </div>
    </article>
  );
}

export default EventDetail;

```

## `frontend/src/components/forms/EventForm.tsx`

```tsx
import {
  useEffect,
  useState,
  type ChangeEvent,
  type FormEvent,
} from "react";
import type {
  Category,
  EventFormData,
  EventFormErrors,
} from "../../types/campus-event";
import { validateEvent } from "../../utils/validate-event";

interface EventFormProps {
  initialData: EventFormData;
  submitText: string;
  onSubmit: (data: EventFormData) => void;
}

const categories: Category[] = ["Seminer", "Atölye", "Söyleşi", "Yarışma"];

function EventForm({ initialData, submitText, onSubmit }: EventFormProps) {
  const [data, setData] = useState<EventFormData>(initialData);
  const [errors, setErrors] = useState<EventFormErrors>({});

  useEffect(() => {
    setData(initialData);
    setErrors({});
  }, [initialData]);

  function handleChange(
    event: ChangeEvent<
      HTMLInputElement | HTMLSelectElement | HTMLTextAreaElement
    >,
  ): void {
    setData({
      ...data,
      [event.target.name]: event.target.value,
    });
  }

  function handleSubmit(event: FormEvent<HTMLFormElement>): void {
    event.preventDefault();
    const found = validateEvent(data);
    setErrors(found);

    if (Object.keys(found).length === 0) {
      onSubmit(data);
    }
  }

  return (
    <form className="form-karti" noValidate onSubmit={handleSubmit}>
      <div className="form-alan">
        <label htmlFor="title">Etkinlik Adı</label>
        <input
          id="title"
          name="title"
          type="text"
          maxLength={80}
          placeholder="Örn. Kariyer Günleri 2026"
          value={data.title}
          onChange={handleChange}
          aria-invalid={errors.title ? true : undefined}
        />
        {errors.title && <span className="hata-metni">{errors.title}</span>}
      </div>

      <div className="form-alan">
        <label htmlFor="category">Kategori</label>
        <select
          id="category"
          name="category"
          value={data.category}
          onChange={handleChange}
          aria-invalid={errors.category ? true : undefined}
        >
          <option value="">Seçiniz</option>
          {categories.map((category) => (
            <option key={category} value={category}>
              {category}
            </option>
          ))}
        </select>
        {errors.category && (
          <span className="hata-metni">{errors.category}</span>
        )}
      </div>

      <div className="form-alan">
        <label htmlFor="date">Tarih</label>
        <input
          id="date"
          name="date"
          type="date"
          value={data.date}
          onChange={handleChange}
          aria-invalid={errors.date ? true : undefined}
        />
        {errors.date && <span className="hata-metni">{errors.date}</span>}
      </div>

      <div className="form-alan">
        <label htmlFor="time">Saat</label>
        <input
          id="time"
          name="time"
          type="time"
          value={data.time}
          onChange={handleChange}
          aria-invalid={errors.time ? true : undefined}
        />
        {errors.time && <span className="hata-metni">{errors.time}</span>}
      </div>

      <div className="form-alan">
        <label htmlFor="location">Yer</label>
        <input
          id="location"
          name="location"
          type="text"
          placeholder="Örn. A Blok Konferans Salonu"
          value={data.location}
          onChange={handleChange}
          aria-invalid={errors.location ? true : undefined}
        />
        {errors.location && (
          <span className="hata-metni">{errors.location}</span>
        )}
      </div>

      <div className="form-alan">
        <label htmlFor="capacity">Kontenjan</label>
        <input
          id="capacity"
          name="capacity"
          type="number"
          min={1}
          max={1000}
          value={data.capacity}
          onChange={handleChange}
          aria-invalid={errors.capacity ? true : undefined}
        />
        {errors.capacity && (
          <span className="hata-metni">{errors.capacity}</span>
        )}
      </div>

      <div className="form-alan">
        <label htmlFor="description">Açıklama</label>
        <textarea
          id="description"
          name="description"
          rows={5}
          value={data.description}
          onChange={handleChange}
          aria-invalid={errors.description ? true : undefined}
        />
        {errors.description && (
          <span className="hata-metni">{errors.description}</span>
        )}
      </div>

      <button className="buton" type="submit">
        {submitText}
      </button>
    </form>
  );
}

export default EventForm;

```

## `frontend/src/context/EventsContext.tsx`

```tsx
import {
  createContext,
  useContext,
  useState,
  type ReactNode,
} from "react";
import { events as initialEvents } from "../data/events";
import type {
  CampusEvent,
  Category,
  EventFormData,
} from "../types/campus-event";

interface EventsContextValue {
  events: CampusEvent[];
  addEvent: (data: EventFormData) => void;
  updateEvent: (id: string, data: EventFormData) => void;
  deleteEvent: (id: string) => void;
}

const EventsContext = createContext<EventsContextValue | null>(null);

interface EventsProviderProps {
  children: ReactNode;
}

function toEvent(id: string, data: EventFormData): CampusEvent {
  return {
    id,
    title: data.title.trim(),
    category: data.category as Category,
    date: data.date,
    time: data.time,
    location: data.location.trim(),
    capacity: Number(data.capacity),
    description: data.description.trim(),
  };
}

export function EventsProvider({ children }: EventsProviderProps) {
  const [events, setEvents] = useState<CampusEvent[]>(initialEvents);

  function addEvent(data: EventFormData): void {
    setEvents((current) => [
      ...current,
      toEvent(`event-${Date.now()}`, data),
    ]);
  }

  function updateEvent(id: string, data: EventFormData): void {
    setEvents((current) =>
      current.map((event) =>
        event.id === id
          ? { ...event, ...toEvent(id, data) }
          : event,
      ),
    );
  }

  function deleteEvent(id: string): void {
    setEvents((current) => current.filter((event) => event.id !== id));
  }

  return (
    <EventsContext.Provider
      value={{ events, addEvent, updateEvent, deleteEvent }}
    >
      {children}
    </EventsContext.Provider>
  );
}

export function useEvents(): EventsContextValue {
  const value = useContext(EventsContext);

  if (value === null) {
    throw new Error("EventsProvider yok");
  }

  return value;
}

```

## `frontend/src/pages/HomePage.tsx`

```tsx
import { Link } from "react-router-dom";
import EventList from "../components/events/EventList";
import { useEvents } from "../context/EventsContext";

function HomePage() {
  const { events } = useEvents();
  const upcoming = [...events]
    .sort((a, b) => a.date.localeCompare(b.date))
    .slice(0, 2);

  return (
    <>
      <section className="intro">
        <h2 className="sayfa-baslik">Yaklaşan 2 Etkinlik</h2>
      </section>
      <EventList events={upcoming} />
      <p className="sayfa-aksiyon">
        <Link className="buton" to="/events">
          Tüm etkinlikleri gör
        </Link>
      </p>
    </>
  );
}

export default HomePage;

```

## `frontend/src/pages/EventsPage.tsx`

```tsx
import { useState } from "react";
import EventFilter from "../components/events/EventFilter";
import EventList from "../components/events/EventList";
import { useEvents } from "../context/EventsContext";
import type { Category } from "../types/campus-event";
import { filterByCategory, searchEvents } from "../utils/filter-events";

function EventsPage() {
  const { events } = useEvents();
  const [searchText, setSearchText] = useState("");
  const [category, setCategory] = useState<Category | "">("");
  const categories = [...new Set(events.map((event) => event.category))];
  const filtered = filterByCategory(
    searchEvents(events, searchText),
    category,
  );

  return (
    <>
      <h2 className="sayfa-baslik">Tüm Etkinlikler</h2>
      <EventFilter
        searchText={searchText}
        category={category}
        categories={categories}
        onSearchChange={setSearchText}
        onCategoryChange={setCategory}
      />
      <p id="sonuc" role="status" aria-live="polite">
        {filtered.length === 0
          ? "Aramanıza uygun etkinlik bulunamadı."
          : `${filtered.length} etkinlik listeleniyor.`}
      </p>
      <EventList
        events={filtered}
        emptyText="Aramanıza uygun etkinlik bulunamadı."
      />
    </>
  );
}

export default EventsPage;

```

## `frontend/src/pages/EventDetailPage.tsx`

```tsx
import { useParams } from "react-router-dom";
import EventDetail from "../components/events/EventDetail";
import { useEvents } from "../context/EventsContext";
import { findEventById } from "../utils/filter-events";
import NotFoundPage from "./NotFoundPage";

function EventDetailPage() {
  const { id } = useParams();
  const { events } = useEvents();
  const event = findEventById(events, id ?? "");

  if (!event) {
    return <NotFoundPage />;
  }

  return (
    <>
      <h2 className="sayfa-baslik">{event.title}</h2>
      <EventDetail event={event} />
    </>
  );
}

export default EventDetailPage;

```

## `frontend/src/pages/AdminPage.tsx`

```tsx
import { Link } from "react-router-dom";
import { useEvents } from "../context/EventsContext";
import { formatDate } from "../utils/format-date";

function AdminPage() {
  const { events, deleteEvent } = useEvents();

  function handleDelete(id: string, title: string): void {
    if (window.confirm(`"${title}" silinsin mi?`)) {
      deleteEvent(id);
    }
  }

  return (
    <>
      <h2 className="sayfa-baslik">Etkinlik Yönetimi</h2>
      <p>
        <Link className="buton" to="/admin/new">
          + Yeni etkinlik
        </Link>
      </p>

      <table className="tablo">
        <thead>
          <tr>
            <th>Etkinlik</th>
            <th>Tarih</th>
            <th>Kategori</th>
            <th>İşlemler</th>
          </tr>
        </thead>
        <tbody>
          {events.map((event) => (
            <tr key={event.id}>
              <td data-baslik="Etkinlik">{event.title}</td>
              <td data-baslik="Tarih">{formatDate(event.date)}</td>
              <td data-baslik="Kategori">{event.category}</td>
              <td className="islemler">
                <Link
                  className="buton"
                  to={`/admin/${event.id}/edit`}
                >
                  Düzenle
                </Link>
                <button
                  className="buton buton-sil"
                  type="button"
                  onClick={() => handleDelete(event.id, event.title)}
                >
                  Sil
                </button>
              </td>
            </tr>
          ))}
        </tbody>
      </table>
    </>
  );
}

export default AdminPage;

```

## `frontend/src/pages/AddEventPage.tsx`

```tsx
import { useNavigate } from "react-router-dom";
import EventForm from "../components/forms/EventForm";
import { useEvents } from "../context/EventsContext";
import type { EventFormData } from "../types/campus-event";

const emptyForm: EventFormData = {
  title: "",
  category: "",
  date: "",
  time: "",
  location: "",
  capacity: "",
  description: "",
};

function AddEventPage() {
  const { addEvent } = useEvents();
  const navigate = useNavigate();

  return (
    <>
      <h2 className="sayfa-baslik">Etkinlik Ekle</h2>
      <EventForm
        initialData={emptyForm}
        submitText="Kaydet"
        onSubmit={(data) => {
          addEvent(data);
          navigate("/admin");
        }}
      />
    </>
  );
}

export default AddEventPage;

```

## `frontend/src/pages/EditEventPage.tsx`

```tsx
import { useMemo } from "react";
import { useNavigate, useParams } from "react-router-dom";
import EventForm from "../components/forms/EventForm";
import { useEvents } from "../context/EventsContext";
import { findEventById } from "../utils/filter-events";
import NotFoundPage from "./NotFoundPage";

function EditEventPage() {
  const { id } = useParams();
  const { events, updateEvent } = useEvents();
  const navigate = useNavigate();
  const event = findEventById(events, id ?? "");

  const initialData = useMemo(
    () =>
      event
        ? {
            title: event.title,
            category: event.category,
            date: event.date,
            time: event.time,
            location: event.location,
            capacity: String(event.capacity),
            description: event.description,
          }
        : null,
    [event],
  );

  if (!event || !initialData) {
    return <NotFoundPage />;
  }

  return (
    <>
      <h2 className="sayfa-baslik">Etkinlik Güncelle</h2>
      <EventForm
        initialData={initialData}
        submitText="Güncelle"
        onSubmit={(data) => {
          updateEvent(event.id, data);
          navigate("/admin");
        }}
      />
    </>
  );
}

export default EditEventPage;

```

## `frontend/src/pages/LoginPage.tsx`

```tsx
import { useState, type FormEvent } from "react";
import { Link } from "react-router-dom";

interface LoginErrors {
  email?: string;
  password?: string;
}

function LoginPage() {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [errors, setErrors] = useState<LoginErrors>({});
  const [sent, setSent] = useState(false);

  function handleSubmit(event: FormEvent<HTMLFormElement>): void {
    event.preventDefault();
    const found: LoginErrors = {};

    if (!email.includes("@")) {
      found.email = "Geçerli bir e-posta girin.";
    }

    if (password.length < 6) {
      found.password = "Şifre en az 6 karakter olmalı.";
    }

    setErrors(found);
    setSent(Object.keys(found).length === 0);
  }

  return (
    <section className="auth-kart">
      <h2 className="sayfa-baslik">Giriş Yap</h2>
      <form noValidate onSubmit={handleSubmit}>
        <div className="form-alan">
          <label htmlFor="login-email">E-posta</label>
          <input
            id="login-email"
            type="email"
            value={email}
            onChange={(event) => setEmail(event.target.value)}
            aria-invalid={errors.email ? true : undefined}
          />
          {errors.email && <span className="hata-metni">{errors.email}</span>}
        </div>

        <div className="form-alan">
          <label htmlFor="login-password">Şifre</label>
          <input
            id="login-password"
            type="password"
            value={password}
            onChange={(event) => setPassword(event.target.value)}
            aria-invalid={errors.password ? true : undefined}
          />
          {errors.password && (
            <span className="hata-metni">{errors.password}</span>
          )}
        </div>

        <button className="buton auth-buton" type="submit">
          Giriş yap
        </button>
      </form>

      {sent && <p className="mesaj basari-kutusu">Gerçek giriş Sprint 10'da</p>}

      <p className="auth-linkler">
        <Link to="/forgot-password">Şifremi unuttum</Link>
        <Link to="/register">Hesabın yok mu? Kayıt ol</Link>
      </p>
    </section>
  );
}

export default LoginPage;

```

## `frontend/src/pages/RegisterPage.tsx`

```tsx
import { useState, type FormEvent } from "react";
import { Link } from "react-router-dom";

interface RegisterErrors {
  name?: string;
  email?: string;
  password?: string;
  password2?: string;
}

function RegisterPage() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [password2, setPassword2] = useState("");
  const [errors, setErrors] = useState<RegisterErrors>({});
  const [sent, setSent] = useState(false);

  function handleSubmit(event: FormEvent<HTMLFormElement>): void {
    event.preventDefault();
    const found: RegisterErrors = {};

    if (name.trim().length < 3) {
      found.name = "Ad soyad en az 3 karakter olmalı.";
    }
    if (!email.includes("@")) {
      found.email = "Geçerli bir e-posta girin.";
    }
    if (password.length < 6) {
      found.password = "Şifre en az 6 karakter olmalı.";
    }
    if (password2 !== password) {
      found.password2 = "Şifreler aynı değil.";
    }

    setErrors(found);
    setSent(Object.keys(found).length === 0);
  }

  return (
    <section className="auth-kart">
      <h2 className="sayfa-baslik">Kayıt Ol</h2>
      <form noValidate onSubmit={handleSubmit}>
        <div className="form-alan">
          <label htmlFor="register-name">Ad Soyad</label>
          <input
            id="register-name"
            type="text"
            value={name}
            onChange={(event) => setName(event.target.value)}
            aria-invalid={errors.name ? true : undefined}
          />
          {errors.name && <span className="hata-metni">{errors.name}</span>}
        </div>

        <div className="form-alan">
          <label htmlFor="register-email">E-posta</label>
          <input
            id="register-email"
            type="email"
            value={email}
            onChange={(event) => setEmail(event.target.value)}
            aria-invalid={errors.email ? true : undefined}
          />
          {errors.email && <span className="hata-metni">{errors.email}</span>}
        </div>

        <div className="form-alan">
          <label htmlFor="register-password">Şifre</label>
          <input
            id="register-password"
            type="password"
            value={password}
            onChange={(event) => setPassword(event.target.value)}
            aria-invalid={errors.password ? true : undefined}
          />
          {errors.password && (
            <span className="hata-metni">{errors.password}</span>
          )}
        </div>

        <div className="form-alan">
          <label htmlFor="register-password2">Şifre (tekrar)</label>
          <input
            id="register-password2"
            type="password"
            value={password2}
            onChange={(event) => setPassword2(event.target.value)}
            aria-invalid={errors.password2 ? true : undefined}
          />
          {errors.password2 && (
            <span className="hata-metni">{errors.password2}</span>
          )}
        </div>

        <button className="buton auth-buton" type="submit">
          Kayıt ol
        </button>
      </form>

      {sent && <p className="mesaj basari-kutusu">Gerçek kayıt Sprint 10'da</p>}

      <p className="auth-linkler">
        <Link to="/login">Zaten hesabın var mı? Giriş yap</Link>
      </p>
    </section>
  );
}

export default RegisterPage;

```

## `frontend/src/pages/ForgotPasswordPage.tsx`

```tsx
import { useState, type FormEvent } from "react";
import { Link } from "react-router-dom";

function ForgotPasswordPage() {
  const [email, setEmail] = useState("");
  const [error, setError] = useState("");
  const [sent, setSent] = useState(false);

  function handleSubmit(event: FormEvent<HTMLFormElement>): void {
    event.preventDefault();
    const found = email.includes("@") ? "" : "Geçerli bir e-posta girin.";

    setError(found);
    setSent(found === "");
  }

  return (
    <section className="auth-kart">
      <h2 className="sayfa-baslik">Şifremi Unuttum</h2>
      <p>
        Kayıtlı e-posta adresinizi yazın, şifre yenileme bağlantısı gönderelim.
      </p>

      {sent && (
        <p className="mesaj basari-kutusu">
          Bağlantı {email} adresine gönderildi (demo).
        </p>
      )}

      <form noValidate onSubmit={handleSubmit}>
        <div className="form-alan">
          <label htmlFor="forgot-email">E-posta</label>
          <input
            id="forgot-email"
            type="email"
            value={email}
            onChange={(event) => setEmail(event.target.value)}
            aria-invalid={error ? true : undefined}
          />
          {error && <span className="hata-metni">{error}</span>}
        </div>

        <button className="buton auth-buton" type="submit">
          Bağlantı gönder
        </button>
      </form>

      <p className="auth-linkler">
        <Link to="/login">← Girişe dön</Link>
      </p>
    </section>
  );
}

export default ForgotPasswordPage;

```

## `frontend/src/pages/NotFoundPage.tsx`

```tsx
import { Link } from "react-router-dom";

function NotFoundPage() {
  return (
    <section className="bulunamadi">
      <h2 className="sayfa-baslik">Sayfa bulunamadı</h2>
      <p>Aradığınız sayfa ya da etkinlik yok.</p>
      <Link className="buton" to="/">
        Ana sayfaya dön
      </Link>
    </section>
  );
}

export default NotFoundPage;

```

## `frontend/src/data/events.ts`

```typescript
import type { CampusEvent } from "../types/campus-event";

export const events: CampusEvent[] = [
  {
    id: "event-1",
    title: "Kariyer Günleri 2026",
    category: "Seminer",
    date: "2026-10-12",
    time: "14:00",
    location: "A Blok Konferans Salonu",
    description: "Mezunlarla kariyer yolculukları ve sektör deneyimleri üzerine söyleşiler.",
    capacity: 120,
    image: "/afis.svg",
  },
  {
    id: "event-2",
    title: "Robotik Atölyesi",
    category: "Atölye",
    date: "2026-10-20",
    time: "10:00",
    location: "Mühendislik Fakültesi Lab-2",
    description: "Temel sensörler, motor kontrolü ve küçük bir robot uygulaması yapılacak.",
    capacity: 30,
  },
  {
    id: "event-3",
    title: "Siber Güvenlik Söyleşisi",
    category: "Söyleşi",
    date: "2026-10-27",
    time: "13:30",
    location: "B Blok Amfi 1",
    description: "Saldırı yüzeyleri, güvenli yazılım geliştirme ve güncel siber tehditler konuşulacak.",
    capacity: 90,
  },
  {
    id: "event-4",
    title: "Web Tasarım Atölyesi",
    category: "Atölye",
    date: "2026-11-05",
    time: "15:00",
    location: "Bilgisayar Laboratuvarı 3",
    description: "HTML, CSS ve responsive tasarım ile küçük bir arayüz geliştirilecek.",
    capacity: 35,
  },
  {
    id: "event-5",
    title: "Kodlama Yarışması",
    category: "Yarışma",
    date: "2026-11-10",
    time: "12:00",
    location: "Mühendislik Fakültesi",
    description: "Takımlar verilen problemlere süre içinde çözümler geliştirerek yarışacak.",
    capacity: 80,
  },
  {
    id: "event-6",
    title: "Yapay Zeka Semineri",
    category: "Seminer",
    date: "2026-11-17",
    time: "11:00",
    location: "A Blok Konferans Salonu",
    description: "Yapay zekanın eğitimde, yazılımda ve günlük hayatta kullanım alanları ele alınacak.",
    capacity: 150,
  },
];

```

## `frontend/src/types/campus-event.ts`

```typescript
export type Category = "Seminer" | "Atölye" | "Söyleşi" | "Yarışma";

export interface CampusEvent {
  id: string;
  title: string;
  category: Category;
  capacity: number;
  date: string;
  time: string;
  location: string;
  description: string;
  image?: string;
}

export interface EventFormData {
  title: string;
  category: Category | "";
  date: string;
  time: string;
  location: string;
  capacity: string;
  description: string;
}

export type EventFormErrors = Partial<Record<keyof EventFormData, string>>;

```

## `frontend/src/utils/filter-events.ts`

```typescript
import type { CampusEvent, Category } from "../types/campus-event";

export function searchEvents(
  list: CampusEvent[],
  text: string,
): CampusEvent[] {
  const q = text.trim().toLocaleLowerCase("tr-TR");

  if (q === "") return list;

  return list.filter((event) => {
    const title = event.title.toLocaleLowerCase("tr-TR");
    const description = event.description.toLocaleLowerCase("tr-TR");

    return title.includes(q) || description.includes(q);
  });
}

export function filterByCategory(
  list: CampusEvent[],
  category: Category | "",
): CampusEvent[] {
  if (category === "") return list;

  return list.filter((event) => event.category === category);
}

export function findEventById(
  list: CampusEvent[],
  id: string,
): CampusEvent | undefined {
  return list.find((event) => event.id === id);
}

```

## `frontend/src/utils/format-date.ts`

```typescript
export function formatDate(dateText: string): string {
  const parts = dateText.split("-").map(Number);
  let date: Date;

  if (dateText.match(/^\d{4}-\d{2}-\d{2}$/)) {
    const [year, month, day] = parts;
    date = new Date(year, month - 1, day);
  } else {
    const [day, month, year] = parts;
    date = new Date(year, month - 1, day);
  }

  return date.toLocaleDateString("tr-TR", {
    day: "numeric",
    month: "long",
    year: "numeric",
  });
}

```

## `frontend/src/utils/validate-event.ts`

```typescript
import type { EventFormData, EventFormErrors } from "../types/campus-event";

export function validateEvent(data: EventFormData): EventFormErrors {
  const errors: EventFormErrors = {};

  if (data.title.trim().length < 3) {
    errors.title = "Etkinlik adı en az 3 karakter olmalı.";
  }

  if (data.category === "") {
    errors.category = "Bir kategori seçin.";
  }

  if (data.date === "") {
    errors.date = "Tarih seçin.";
  }

  if (data.time === "") {
    errors.time = "Saat seçin.";
  }

  if (data.location.trim() === "") {
    errors.location = "Yer boş olamaz.";
  }

  const capacity = Number(data.capacity);
  if (
    !Number.isInteger(capacity) ||
    capacity < 1 ||
    capacity > 1000
  ) {
    errors.capacity = "1 ile 1000 arası tam sayı girin.";
  }

  if (data.description.trim().length < 10) {
    errors.description = "Açıklama en az 10 karakter olmalı.";
  }

  return errors;
}

```
