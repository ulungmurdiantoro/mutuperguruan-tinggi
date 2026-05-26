# BLUEPRINT REDESIGN v2.0
## mutuperguruantinggi.id — Multi-Page Architecture + SEO-First + Backend CMS

> **Versi**: 2.0 (Multi-Page Edition)
> **Tanggal**: Mei 2026
> **Pemilik**: PT Padma Global Nusatama
> **Stack Rekomendasi**: Next.js 14 (App Router) + Strapi/Payload CMS + PostgreSQL

---

# DAFTAR ISI

1. [Tujuan & Filosofi Desain](#1-tujuan--filosofi-desain)
2. [Arsitektur Informasi (Sitemap Lengkap)](#2-arsitektur-informasi-sitemap-lengkap)
3. [Detail Per-Halaman (Konten, Layout, CTA)](#3-detail-per-halaman)
4. [Strategi SEO (Technical + On-Page + Content)](#4-strategi-seo)
5. [Skema URL & Internal Linking](#5-skema-url--internal-linking)
6. [Schema.org & Structured Data](#6-schemaorg--structured-data)
7. [Arsitektur Backend & CMS](#7-arsitektur-backend--cms)
8. [Skema Database (ERD)](#8-skema-database-erd)
9. [API Endpoints (REST + Optional GraphQL)](#9-api-endpoints)
10. [Roles, Permissions & Workflow](#10-roles-permissions--workflow)
11. [Stack Teknologi & Deployment](#11-stack-teknologi--deployment)
12. [Roadmap Implementasi (8 Sprint / 16 Minggu)](#12-roadmap-implementasi)

---

## 1. TUJUAN & FILOSOFI DESAIN

### 1.1 Tujuan Bisnis
1. **Authority SEO** → ranking #1 untuk keyword: "SPMI", "AMI", "OBE", "Sertifikasi KAN Perguruan Tinggi", "ISO 21001 Perguruan Tinggi", "Akreditasi PT".
2. **Lead Generation** → konversi pengunjung menjadi peserta pelatihan & mitra institusi.
3. **Content Authority** → menjadi rujukan #1 mutu pendidikan tinggi Indonesia via blog & resource library.
4. **Operational Scalability** → tim non-teknis (marketing/admin) bisa CRUD konten tanpa developer.

### 1.2 Filosofi Multi-Page
- **Satu halaman = satu intent** (search intent matching).
- **Setiap layanan punya landing page sendiri** → menjaring keyword spesifik.
- **Pillar-cluster content model** → halaman pilar (broad) menaungi artikel cluster (specific).
- **Modular component-based** → komponen UI reusable dipakai di banyak halaman.

### 1.3 Prinsip Desain
- **Mobile-first** (50%+ traffic dari mobile)
- **Core Web Vitals friendly** (LCP < 2.5s, FID < 100ms, CLS < 0.1)
- **Accessibility WCAG 2.1 AA**
- **Brand-faithful**: Navy `#0A2558` + Gold `#FFC72C`
- **Formal-akademik**: tone konten konsisten

---

## 2. ARSITEKTUR INFORMASI (SITEMAP LENGKAP)

### 2.1 Struktur Hierarki

```
mutuperguruantinggi.id/
│
├── / (Beranda)
│
├── /tentang-kami
│   ├── /tentang-kami/profil-perusahaan
│   ├── /tentang-kami/visi-misi
│   ├── /tentang-kami/perjalanan
│   ├── /tentang-kami/pakar-kami
│   └── /tentang-kami/legalitas
│
├── /layanan (Pillar page)
│   ├── /layanan/sertifikasi-kompetensi-kan
│   │   ├── /layanan/sertifikasi-kompetensi-kan/lead-implementer-spmi-iso-21001
│   │   ├── /layanan/sertifikasi-kompetensi-kan/auditor-internal-spmi-iso-21001
│   │   ├── /layanan/sertifikasi-kompetensi-kan/tot-outcome-based-education
│   │   ├── /layanan/sertifikasi-kompetensi-kan/implementer-tata-kelola-pt
│   │   ├── /layanan/sertifikasi-kompetensi-kan/auditor-internal-laboratorium-17025
│   │   └── /layanan/sertifikasi-kompetensi-kan/lead-implementer-laboratorium-17025
│   │
│   ├── /layanan/ami-digital
│   ├── /layanan/mitra-spmi-tata-kelola
│   ├── /layanan/mitra-ami
│   ├── /layanan/mitra-kurikulum-obe
│   ├── /layanan/mitra-akreditasi-internasional-acquin
│   ├── /layanan/mitra-akreditasi-nasional
│   ├── /layanan/mitra-iso-21001
│   ├── /layanan/mitra-iso-9001
│   ├── /layanan/mitra-laboratorium-17025
│   └── /layanan/sertifikasi-dosen-tendik
│
├── /event (Listing semua event)
│   ├── /event/[slug-event] (Detail event dinamis)
│   ├── /event/kategori/webinar
│   ├── /event/kategori/bootcamp
│   ├── /event/kategori/sertifikasi
│   └── /event/kategori/in-house-training
│
├── /paket
│   ├── /paket/reguler
│   └── /paket/premium
│
├── /pakar (Listing semua pakar)
│   └── /pakar/[slug-pakar] (Detail profil pakar)
│
├── /artikel (Pillar blog)
│   ├── /artikel/[slug-artikel] (Detail artikel)
│   ├── /artikel/kategori/spmi
│   ├── /artikel/kategori/ami
│   ├── /artikel/kategori/obe
│   ├── /artikel/kategori/tata-kelola
│   ├── /artikel/kategori/akreditasi
│   ├── /artikel/kategori/iso
│   ├── /artikel/kategori/regulasi
│   └── /artikel/tag/[slug-tag]
│
├── /resource (Lead magnets)
│   ├── /resource/template-sop-form
│   ├── /resource/materi-edukasi
│   ├── /resource/ebook
│   └── /resource/[slug-resource]
│
├── /studi-kasus (Case studies)
│   └── /studi-kasus/[slug-case]
│
├── /tools (Tools interaktif)
│   ├── /tools/cek-status-mutu-prodi
│   ├── /tools/cek-status-mutu-pt
│   └── /tools/kalkulator-skor-akreditasi
│
├── /referral-program
├── /call-for-experts
├── /konsultasi-gratis (Lead form khusus)
├── /kontak
├── /faq
├── /karier
│
├── /kebijakan-privasi
├── /syarat-ketentuan
├── /peta-situs (sitemap untuk user)
│
└── /search (Hasil pencarian internal)
```

### 2.2 Total Halaman Statis + Dinamis
| Tipe | Jumlah | Keterangan |
|------|--------|------------|
| Static landing pages | 25 | Beranda, layanan, paket, tools, dll |
| Dynamic content pages | ∞ | Event, artikel, pakar, resource, studi kasus |
| Estimasi total saat launch | 80+ | 25 static + 50+ artikel + 12 pakar + 10 event |
| Target 6 bulan | 200+ | Pertumbuhan konten 30+ artikel/bulan |

---

## 3. DETAIL PER-HALAMAN

### 3.1 BERANDA (`/`)
**SEO Target**: "mutu perguruan tinggi", "pelatihan SPMI Indonesia"
**Sections**: (sudah dibangun di mockup v1)
- Hero + CTA WhatsApp/Event
- Statistik & kredibilitas (counter animasi)
- Event terdekat (3-6 cards)
- Layanan utama (2 big cards)
- Cakupan layanan mitra (8 cards)
- Paket Reguler vs Premium
- Pakar Kami (showcase 8 dari 12)
- CTA Konsultasi Gratis
- 6 Alasan Memilih Kami
- AMI Digital showcase
- Sertifikasi KAN banner
- Timeline perjalanan
- Resource gratis
- Blog terbaru
- Footer

---

### 3.2 HALAMAN LAYANAN (Pillar — `/layanan`)
**Tujuan**: hub untuk semua layanan, internal linking ke semua sub-halaman.
**Sections**:
- Hero: "Solusi Komprehensif Mutu Perguruan Tinggi"
- Tab/Filter: Sertifikasi · Pendampingan · Aplikasi Digital · Akreditasi
- Grid layanan lengkap (16 kartu dengan deskripsi)
- Comparison matrix (Reguler vs Premium vs Custom)
- FAQ layanan umum
- CTA: "Tidak yakin layanan mana? Konsultasi gratis"

---

### 3.3 DETAIL SKEMA SERTIFIKASI (Contoh: `/layanan/sertifikasi-kompetensi-kan/lead-implementer-spmi-iso-21001`)
**SEO Target**: "Lead Implementer SPMI ISO 21001", "Sertifikasi CQAI", "Pelatihan SPMI Berbasis Risiko"

**Sections**:
1. **Hero**:
   - Breadcrumb: Beranda > Layanan > Sertifikasi KAN > Lead Implementer SPMI
   - Title: "Pelatihan 40 JP & Sertifikasi Lead Implementer SPMI Terintegrasi ISO 21001"
   - Badge: "Pertama di Indonesia · KAN Certified"
   - Gelar non-akademik: CQAI (Certified Quality Assurance Implementer)
   - CTA: Daftar + Konsultasi
2. **Overview & manfaat** (kenapa skema ini penting)
3. **Materi pelatihan** (detail dari hal 12 compro)
4. **Benefit lengkap** (sertifikat, gelar, materi, template, forum)
5. **Trainer/Pakar** (3-4 pakar yang menangani skema ini)
6. **Tabel paket** (Reguler vs Premium spesifik untuk skema ini)
7. **Jadwal pelatihan terdekat**
8. **Testimoni alumni** (carousel)
9. **FAQ spesifik skema**
10. **Related schemes** (link ke skema lain)
11. **CTA: Daftar / Tanya / Download brosur**

> **Template ini dipakai untuk 6 skema sertifikasi KAN dengan konten yang disesuaikan.**

---

### 3.4 AMI DIGITAL (`/layanan/ami-digital`)
**SEO Target**: "AMI Digital", "Audit Mutu Internal Digital", "software audit mutu perguruan tinggi"

**Sections**:
1. Hero dengan video demo + CTA "Coba Gratis"
2. Problem-solution narrative (sistem kebut sebulan vs AMI Digital)
3. Fitur utama (6 keunggulan + screenshot)
4. Cara kerja (3-4 step flow)
5. Use case per role (Kaprodi, Auditor, LPM)
6. Pricing & paket
7. Testimoni implementasi (UNSIKA, UMBY, dll)
8. FAQ teknis
9. Request demo form

---

### 3.5 EVENT LISTING (`/event`)
**SEO Target**: "pelatihan SPMI 2026", "webinar perguruan tinggi", "bootcamp OBE"

**Layout**:
- Hero ringkas: "Jadwal Event & Pelatihan 2026"
- Filter sidebar:
  - Kategori (Webinar, Bootcamp, Sertifikasi, IHT, Workshop)
  - Bulan (dropdown)
  - Lokasi (Online, Semarang, Jakarta, dll)
  - Harga (Gratis, Berbayar)
- Grid event (12 per halaman, pagination/infinite scroll)
- Sort: Terdekat / Terbaru / Termurah / Terpopuler
- Sidebar: Newsletter signup, event highlight, kategori populer

---

### 3.6 DETAIL EVENT (`/event/[slug]`)
**Sections**:
1. Hero gambar + judul + meta (tanggal, lokasi, harga, kategori)
2. Sticky sidebar dengan tombol "Daftar Sekarang"
3. Deskripsi event (rich text)
4. Materi yang dibahas
5. Pembicara/trainer
6. Jadwal & lokasi
7. Benefit peserta
8. FAQ
9. Event terkait (3 cards)
10. Schema markup `Event` (untuk Google Rich Results!)

---

### 3.7 ARTIKEL LISTING (Blog — `/artikel`)
**SEO Target**: pillar untuk topical authority

**Layout**:
- Hero search bar + filter kategori
- Featured article (1 besar)
- Grid artikel (12 per halaman)
- Sidebar: Trending, kategori, tag cloud, newsletter
- Pagination

---

### 3.8 DETAIL ARTIKEL (`/artikel/[slug]`)
**Sections**:
1. Hero: judul + author + tanggal + reading time + breadcrumb
2. Featured image
3. Table of contents (sticky di sidebar untuk artikel panjang)
4. Body article (rich text dengan heading, gambar, quote, code, table)
5. Author bio box
6. Tags + share buttons (WA, Twitter, LinkedIn, FB)
7. Related articles (3 cards)
8. Comment section (opsional — bisa pakai Disqus atau native)
9. Newsletter signup inline
10. Schema markup `Article`

---

### 3.9 PAKAR LISTING (`/pakar`)
- Hero: "12 Pakar Kompeten di Bidangnya"
- Filter by spesialisasi: SPMI · AMI · OBE · Tata Kelola · ISO · Akreditasi
- Grid 12+ pakar (card dengan foto, nama, role, afiliasi)

### 3.10 DETAIL PAKAR (`/pakar/[slug]`)
- Hero: foto besar + nama + role + afiliasi
- Bio lengkap
- Spesialisasi (tag)
- Publikasi/karya ilmiah
- Event yang dibawakan (auto-pull)
- Schema markup `Person`

---

### 3.11 STUDI KASUS (`/studi-kasus`)
**SEO Magnet**: bukti sosial untuk konversi B2B

**Template tiap case**:
1. Hero: nama PT mitra + logo + ringkasan hasil
2. Challenge (masalah awal)
3. Approach (solusi yang diberikan)
4. Result (angka konkret: skor akreditasi naik, dll)
5. Quote dari pimpinan PT
6. Layanan yang dipakai (link ke halaman layanan)
7. Schema markup `CaseStudy` (custom)

**Contoh case** (dari compro):
- ISO 9001:2015 — FBS UNNES
- ACQUIN — UIN Walisongo
- AMI Digital — UNSIKA
- Laboratorium 17025:2017 — UIN Walisongo
- SPMI — UIN Banten
- Laboratorium 17025:2017 — UNSIL

---

### 3.12 TOOLS INTERAKTIF (`/tools/cek-status-mutu-prodi`)
**Lead magnet** — multi-step form
1. Step 1: Identitas PT & Prodi
2. Step 2: 20 pertanyaan checklist mutu
3. Step 3: Hasil (dengan skor estimasi + rekomendasi)
4. Capture email untuk download laporan lengkap

---

### 3.13 KONSULTASI GRATIS (`/konsultasi-gratis`)
**Conversion-focused page**:
- Hero dengan foto pakar
- Form pendaftaran (nama, institusi, jabatan, email, WA, topik, tanggal preferensi)
- Trust signals (testimoni pendek, statistik)
- "Apa yang Akan Anda Dapatkan" (3-4 point)
- Daftar pakar yang akan menangani

---

## 4. STRATEGI SEO

### 4.1 Technical SEO

| Aspek | Target | Implementasi |
|-------|--------|--------------|
| **Page Speed** | LCP < 2.5s | Next.js SSG/ISR, image optimization (next/image), CDN |
| **Mobile-friendly** | 100% responsive | Mobile-first CSS, viewport meta tag |
| **HTTPS** | Wajib | SSL via Cloudflare/Let's Encrypt |
| **XML Sitemap** | Auto-generated | next-sitemap atau custom generator |
| **Robots.txt** | Allow crawler, block admin | Auto-generated per environment |
| **Canonical URLs** | Semua halaman | `<link rel="canonical">` di setiap page |
| **hreflang** | Hanya `id` saat ini | Siap ditambahkan saat multilingual |
| **Structured Data** | Schema.org semua tipe | JSON-LD di setiap halaman |
| **Core Web Vitals** | Green semua | Monitoring via PageSpeed Insights & Search Console |

### 4.2 On-Page SEO Per Halaman

**Setiap halaman wajib punya**:
1. **Unique title tag** (50-60 karakter)
   - Format: `[Page Specific] | mutuperguruantinggi.id`
2. **Meta description** (150-160 karakter) — value proposition + CTA
3. **H1 unik** — hanya satu per halaman, mengandung primary keyword
4. **Heading hierarchy** — H1 → H2 → H3 (tidak lompat)
5. **Alt text** semua gambar (deskriptif, mengandung keyword saat relevan)
6. **Internal links** — minimal 3-5 link ke halaman terkait
7. **External authority links** — link ke regulasi resmi (Kemdiktisaintek, BAN-PT)
8. **URL slug**: lowercase, kata dipisah dash, mengandung keyword
9. **Open Graph + Twitter Card** untuk social sharing

**Contoh meta untuk halaman SPMI**:
```html
<title>Sertifikasi Lead Implementer SPMI Terintegrasi ISO 21001 (CQAI) | mutuperguruantinggi.id</title>
<meta name="description" content="Pelatihan 40 JP + Sertifikasi KAN Lead Implementer SPMI berbasis risiko, sesuai Permendiktisaintek No. 39/2025. Pertama di Indonesia. Daftar sekarang!">
<meta name="keywords" content="Lead Implementer SPMI, sertifikasi ISO 21001, CQAI, pelatihan SPMI Indonesia, Permendiktisaintek 39">
```

### 4.3 Content SEO — Pillar-Cluster Model

**Pillar Pages** (broad, 3000-5000 kata):
1. "Panduan Lengkap SPMI untuk Perguruan Tinggi Indonesia" → `/artikel/panduan-spmi-perguruan-tinggi`
2. "Audit Mutu Internal: Konsep, Prinsip & Implementasi" → `/artikel/panduan-ami`
3. "Outcome-Based Education (OBE): Panduan untuk Dosen" → `/artikel/panduan-obe`
4. "ISO 21001:2018 untuk Lembaga Pendidikan" → `/artikel/panduan-iso-21001`
5. "Akreditasi Perguruan Tinggi & Program Studi" → `/artikel/panduan-akreditasi`
6. "Tata Kelola Perguruan Tinggi (GUG)" → `/artikel/panduan-tata-kelola-pt`

**Cluster Articles** (specific, 1000-2000 kata) — masing-masing 10-15 artikel per pilar:
- Contoh untuk pilar SPMI:
  - "Permendiktisaintek No. 39 Tahun 2025: Yang Perlu Diketahui"
  - "Siklus PPEPP dalam SPMI: Step by Step"
  - "Perbedaan SPMI dan SPME"
  - "Template Dokumen SPMI Berbasis Risiko"
  - dst.

### 4.4 Target Keyword Strategy

**Primary Keywords** (high search volume, high competition):
- SPMI perguruan tinggi
- Sertifikasi KAN
- ISO 21001 pendidikan
- AMI Audit Mutu Internal
- OBE Outcome Based Education
- Akreditasi perguruan tinggi
- Pelatihan SPMI

**Long-tail Keywords** (lower volume, easier to rank):
- "pelatihan auditor internal SPMI bersertifikat KAN"
- "implementasi Permendiktisaintek 39 2025"
- "perbedaan SPMI dan akreditasi"
- "biaya sertifikasi lead implementer SPMI"
- "template dokumen SPMI berbasis risiko gratis"

**Local SEO Keywords**:
- "pelatihan SPMI Semarang"
- "lembaga pelatihan mutu PT Jawa Tengah"
- "konsultan akreditasi perguruan tinggi"

### 4.5 Off-Page SEO
- **Backlink dari PT mitra**: minta link dari halaman "mitra" di website kampus mitra
- **Guest post** di portal pendidikan (kompas.com edu, detik edu, dll)
- **Press release** untuk milestone (akreditasi KAN, kerjasama baru)
- **YouTube channel** untuk reuse konten webinar → embed di website
- **LinkedIn articles** pakar (Dr. Agung, Prof. Joko, dll) link ke website

---

## 5. SKEMA URL & INTERNAL LINKING

### 5.1 URL Naming Convention
```
DO:
✓ /layanan/sertifikasi-kompetensi-kan
✓ /artikel/panduan-implementasi-spmi-2026
✓ /pakar/dr-agung-yulianto

DON'T:
✗ /page?id=123
✗ /Layanan/SPMI
✗ /artikel/panduan_implementasi_spmi
```

### 5.2 Breadcrumb di Semua Halaman
```
Beranda > Layanan > Sertifikasi KAN > Lead Implementer SPMI ISO 21001
```
Schema markup `BreadcrumbList` wajib.

### 5.3 Internal Linking Rules
- Setiap artikel cluster wajib link ke pillar parent
- Setiap halaman layanan wajib link ke 2-3 layanan terkait
- Setiap detail event wajib link ke kategori parent + layanan yang relevan
- Footer: link ke 10-15 halaman penting (helps SEO juice flow)
- "Halaman terkait" otomatis di bawah konten

---

## 6. SCHEMA.ORG & STRUCTURED DATA

### 6.1 Tipe Schema per Halaman

| Halaman | Schema |
|---------|--------|
| Beranda | `Organization`, `WebSite` (dengan SearchAction) |
| /tentang-kami | `AboutPage`, `Organization` |
| /layanan/* | `Service`, `EducationalOccupationalProgram` |
| /event | `ItemList` |
| /event/[slug] | `Event` (penting untuk Rich Results!) |
| /artikel/[slug] | `Article` atau `BlogPosting` |
| /pakar/[slug] | `Person` |
| /studi-kasus/[slug] | `Article` (case study) |
| /faq | `FAQPage` |
| All pages | `BreadcrumbList` |

### 6.2 Contoh Schema untuk Event
```json
{
  "@context": "https://schema.org",
  "@type": "Event",
  "name": "Bootcamp Lead Implementer SPMI ISO 21001",
  "startDate": "2026-05-20T09:00:00+07:00",
  "endDate": "2026-05-25T16:00:00+07:00",
  "eventStatus": "https://schema.org/EventScheduled",
  "eventAttendanceMode": "https://schema.org/MixedEventAttendanceMode",
  "location": [
    {
      "@type": "VirtualLocation",
      "url": "https://mutuperguruantinggi.id/event/bootcamp-spmi"
    },
    {
      "@type": "Place",
      "name": "Kantor mutuperguruantinggi.id",
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "Jl. Teras Bali No.12",
        "addressLocality": "Mijen",
        "addressRegion": "Semarang"
      }
    }
  ],
  "offers": {
    "@type": "Offer",
    "price": "3750000",
    "priceCurrency": "IDR",
    "url": "https://mutuperguruantinggi.id/event/bootcamp-spmi/daftar",
    "availability": "https://schema.org/InStock"
  },
  "performer": {
    "@type": "Person",
    "name": "Dr. Agung Yulianto, M.Si."
  },
  "organizer": {
    "@type": "Organization",
    "name": "mutuperguruantinggi.id",
    "url": "https://mutuperguruantinggi.id"
  }
}
```

---

## 7. ARSITEKTUR BACKEND & CMS

### 7.1 Pilihan Stack (Rekomendasi)

**Opsi A — Headless CMS (Recommended untuk skala)** ⭐
```
Frontend: Next.js 14 (App Router) + Tailwind CSS
CMS: Strapi (open source, self-hosted) atau Payload CMS
Database: PostgreSQL
Storage: Cloudflare R2 atau AWS S3 (media)
Cache: Redis (untuk session, rate limiting)
Search: Meilisearch atau Algolia
Email: Resend atau SendGrid
Hosting Frontend: Vercel / Cloudflare Pages
Hosting CMS: VPS (DigitalOcean / Hetzner) atau Railway
```

**Opsi B — Monolithic (Lebih mudah maintain)**
```
Stack: Laravel 11 + Filament v3 (admin panel)
Database: MySQL/PostgreSQL
Cache: Redis
Search: Laravel Scout + Meilisearch
Hosting: VPS dengan Laravel Forge
```

**Opsi C — WordPress (Familiar untuk tim non-teknis)**
```
WordPress + ACF Pro + Custom Post Types
Theme: Custom dari mockup HTML
Plugins: Yoast SEO, RankMath, WP Rocket
```

> **Rekomendasi**: **Opsi A (Next.js + Strapi)** karena: (1) SEO terbaik (SSG/ISR), (2) skalabilitas tinggi, (3) developer experience modern, (4) admin panel Strapi user-friendly untuk tim marketing.

### 7.2 Diagram Arsitektur

```
┌─────────────────────────────────────────────────────────────┐
│                        USER BROWSER                          │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                  CDN (Cloudflare)                            │
│  · Static assets caching   · DDoS protection                 │
│  · Image optimization      · Edge functions                  │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│              FRONTEND (Next.js on Vercel)                    │
│  · SSG (Static): /tentang, /layanan, /paket                 │
│  · ISR (Incremental): /event, /artikel, /pakar              │
│  · SSR (Server): /search, /tools                            │
│  · API Routes: /api/contact, /api/subscribe                 │
└──────────────────────────┬──────────────────────────────────┘
                           │  REST/GraphQL
                           ▼
┌─────────────────────────────────────────────────────────────┐
│           CMS BACKEND (Strapi on VPS/Railway)                │
│  · Admin panel (kelola konten)                               │
│  · REST API + GraphQL                                        │
│  · Role-based access control                                 │
│  · Media library                                             │
│  · Workflow & permissions                                    │
└──────────┬─────────────────────────────────────┬────────────┘
           │                                     │
           ▼                                     ▼
┌──────────────────────┐              ┌────────────────────────┐
│  PostgreSQL Database │              │  Object Storage (R2/S3)│
│  · Content tables    │              │  · Images              │
│  · User tables       │              │  · PDFs                │
│  · Audit logs        │              │  · Videos              │
└──────────────────────┘              └────────────────────────┘
           │
           ▼
┌─────────────────────────────────────────────────────────────┐
│                  INTEGRATIONS                                │
│  · Email (Resend)          · WhatsApp Business API           │
│  · Payment (Midtrans/Xendit) · Analytics (GA4, Plausible)   │
│  · Search (Meilisearch)    · Captcha (Cloudflare Turnstile) │
│  · Mailchimp/Brevo (newsletter)                              │
└─────────────────────────────────────────────────────────────┘
```

### 7.3 Modular Component Architecture

**Reusable React Components** (frontend):
```
components/
├── ui/ (atoms)
│   ├── Button.tsx
│   ├── Input.tsx
│   ├── Card.tsx
│   ├── Badge.tsx
│   └── ...
├── sections/ (molecules)
│   ├── HeroSection.tsx
│   ├── StatsSection.tsx
│   ├── EventCard.tsx
│   ├── ExpertCard.tsx
│   ├── ArticleCard.tsx
│   ├── PackageCard.tsx
│   └── ...
├── layouts/
│   ├── PageLayout.tsx
│   ├── ArticleLayout.tsx
│   └── ServiceLayout.tsx
└── blocks/ (CMS dynamic blocks)
    ├── RichTextBlock.tsx
    ├── ImageBlock.tsx
    ├── CTABlock.tsx
    ├── FAQBlock.tsx
    └── EmbedBlock.tsx
```

**Page Builder di CMS**: admin bisa drag-drop block-block ini untuk membuat custom landing page tanpa coding.

---

## 8. SKEMA DATABASE (ERD)

### 8.1 Tabel Utama

```sql
-- ====================================================
-- USERS & AUTH
-- ====================================================
users
├── id (PK)
├── email (unique)
├── password_hash
├── name
├── phone
├── role (enum: super_admin, admin, editor, author, subscriber)
├── avatar_url
├── created_at
└── updated_at

-- ====================================================
-- CONTENT: SERVICES (Layanan)
-- ====================================================
services
├── id (PK)
├── slug (unique)
├── name
├── tagline
├── description (rich text)
├── icon
├── category (enum: sertifikasi, pendampingan, aplikasi, mitra)
├── is_featured (boolean)
├── order_index
├── meta_title
├── meta_description
├── og_image_url
├── schema_data (json)
├── parent_service_id (nullable, untuk sub-service)
├── created_at
└── updated_at

-- ====================================================
-- CERTIFICATION SCHEMES (Skema KAN)
-- ====================================================
certification_schemes
├── id (PK)
├── slug
├── name (e.g. "Lead Implementer SPMI Terintegrasi ISO 21001")
├── code (e.g. "EDUKIA-IMR-2024-003")
├── degree_title (e.g. "CQAI")
├── degree_full (e.g. "Certified Quality Assurance Implementer")
├── duration_hours (e.g. 40)
├── description
├── materials (json — list materi)
├── benefits (json — list benefit)
├── prerequisites (json)
├── sector (enum: perguruan_tinggi, laboratorium, lainnya)
├── lsp_partner (e.g. "LSP EDUKIA")
├── price_regular
├── price_premium
├── meta_*
└── timestamps

-- ====================================================
-- EVENTS
-- ====================================================
events
├── id (PK)
├── slug
├── title
├── subtitle
├── description (rich text)
├── category_id (FK -> event_categories)
├── start_date
├── end_date
├── location_type (enum: online, offline, hybrid)
├── venue_name
├── venue_address
├── meeting_link
├── max_participants
├── current_participants
├── price
├── early_bird_price
├── early_bird_until
├── registration_deadline
├── status (enum: upcoming, ongoing, completed, cancelled)
├── is_featured
├── thumbnail_url
├── banner_url
├── gallery (json array)
├── benefits (json)
├── certificate_type
├── related_scheme_id (FK -> certification_schemes, nullable)
├── meta_*
├── schema_data (json)
└── timestamps

event_categories
├── id (PK)
├── slug
├── name (e.g. "Webinar Nasional")
├── description
├── icon
└── order_index

event_speakers (many-to-many: events <-> experts)
├── event_id (FK)
├── expert_id (FK)
├── role (e.g. "Trainer Utama", "Moderator")
└── PRIMARY KEY (event_id, expert_id)

event_registrations
├── id (PK)
├── event_id (FK)
├── user_id (FK, nullable jika guest)
├── name, email, phone, institution, position
├── payment_status (enum: pending, paid, failed, refunded)
├── payment_method
├── payment_amount
├── payment_ref
├── package_type (enum: regular, premium)
├── certificate_issued (boolean)
├── certificate_url
├── created_at
└── updated_at

-- ====================================================
-- EXPERTS / TRAINERS
-- ====================================================
experts
├── id (PK)
├── slug
├── name (e.g. "Dr. Agung Yulianto, M.Si.")
├── photo_url
├── current_position (e.g. "Wakil Dekan I FEB UNNES")
├── affiliation (e.g. "Universitas Negeri Semarang")
├── role_label (e.g. "Pakar SPMI, OBE, AMI")
├── bio (rich text)
├── education (json array)
├── certifications (json array)
├── publications (json array)
├── linkedin_url
├── scholar_url
├── orcid
├── is_active
├── is_featured
├── order_index
├── meta_*
└── timestamps

expert_specializations (many-to-many)
├── expert_id (FK)
├── specialization_id (FK)
└── PRIMARY KEY (expert_id, specialization_id)

specializations
├── id (PK)
├── slug
├── name (e.g. "SPMI", "OBE", "AMI")
└── description

-- ====================================================
-- ARTICLES / BLOG
-- ====================================================
articles
├── id (PK)
├── slug
├── title
├── subtitle
├── excerpt (max 200 char)
├── content (rich text / markdown)
├── featured_image_url
├── featured_image_alt
├── author_id (FK -> users)
├── category_id (FK -> article_categories)
├── reading_time_minutes
├── view_count
├── like_count
├── is_featured
├── is_pillar (boolean — penanda pillar page)
├── parent_pillar_id (FK -> articles, nullable — untuk cluster)
├── status (enum: draft, review, published, archived)
├── published_at
├── meta_title
├── meta_description
├── og_image_url
├── canonical_url
├── schema_data (json)
└── timestamps

article_categories
├── id (PK)
├── slug
├── name
├── description
├── parent_id (FK -> article_categories, nullable)
└── meta_*

article_tags
├── id (PK)
├── slug
├── name
└── meta_*

article_tag_pivot (many-to-many)
├── article_id (FK)
├── tag_id (FK)
└── PRIMARY KEY (article_id, tag_id)

-- ====================================================
-- RESOURCES (Lead Magnets)
-- ====================================================
resources
├── id (PK)
├── slug
├── title
├── description
├── category (enum: template, ebook, modul, panduan, sop)
├── thumbnail_url
├── file_url (private, hanya bisa diakses setelah subscribe)
├── file_size_bytes
├── file_format (pdf, docx, xlsx, zip)
├── download_count
├── is_gated (boolean — perlu email untuk download)
├── meta_*
└── timestamps

resource_downloads (lead capture)
├── id (PK)
├── resource_id (FK)
├── name, email, phone, institution, position
├── created_at
└── ip_address

-- ====================================================
-- PARTNERS (PT Mitra)
-- ====================================================
partners
├── id (PK)
├── slug
├── name (e.g. "Universitas Negeri Semarang")
├── short_name (e.g. "UNNES")
├── logo_url
├── website_url
├── description
├── type (enum: universitas, institut, politeknik, sekolah_tinggi, akademi)
├── city
├── province
├── services_used (json — array layanan yang dipakai)
├── partnership_since (date)
├── is_featured
├── order_index
└── timestamps

-- ====================================================
-- CASE STUDIES
-- ====================================================
case_studies
├── id (PK)
├── slug
├── title
├── partner_id (FK -> partners)
├── service_id (FK -> services)
├── challenge (rich text)
├── approach (rich text)
├── result (rich text)
├── result_metrics (json — array {label, value})
├── testimonial_text
├── testimonial_author_name
├── testimonial_author_position
├── featured_image_url
├── gallery (json)
├── is_featured
├── meta_*
└── timestamps

-- ====================================================
-- TESTIMONIALS
-- ====================================================
testimonials
├── id (PK)
├── author_name
├── author_position
├── author_institution
├── author_photo_url
├── content
├── rating (1-5)
├── related_service_id (FK, nullable)
├── related_event_id (FK, nullable)
├── is_featured
├── is_published
├── order_index
└── timestamps

-- ====================================================
-- PACKAGES (Paket Pelatihan)
-- ====================================================
packages
├── id (PK)
├── slug
├── name (e.g. "Paket Reguler", "Paket Premium")
├── tagline
├── price
├── price_unit (e.g. "per peserta")
├── description
├── features (json — array {label, included: boolean})
├── is_recommended (boolean — flag "Paling Dipilih")
├── cta_label
├── cta_url
├── order_index
└── timestamps

-- ====================================================
-- FAQS
-- ====================================================
faqs
├── id (PK)
├── question
├── answer (rich text)
├── category (enum: umum, layanan, event, pembayaran, sertifikat)
├── related_service_id (FK, nullable)
├── related_event_id (FK, nullable)
├── order_index
├── is_published
└── timestamps

-- ====================================================
-- LEADS (Konsultasi Form)
-- ====================================================
leads
├── id (PK)
├── name, email, phone
├── institution
├── position
├── topic (enum: spmi, ami, obe, akreditasi, iso, lainnya)
├── message
├── preferred_date
├── source (e.g. "konsultasi-gratis", "footer-form", "popup")
├── status (enum: new, contacted, qualified, converted, lost)
├── assigned_to (FK -> users — admin yang handle)
├── notes (rich text)
├── utm_source, utm_medium, utm_campaign (tracking)
└── timestamps

-- ====================================================
-- NEWSLETTER SUBSCRIBERS
-- ====================================================
subscribers
├── id (PK)
├── email (unique)
├── name (nullable)
├── institution (nullable)
├── interests (json — array kategori interest)
├── source (e.g. "footer", "popup", "resource-download")
├── is_active
├── unsubscribed_at
└── timestamps

-- ====================================================
-- REFERRAL PROGRAM
-- ====================================================
referrals
├── id (PK)
├── referrer_user_id (FK -> users)
├── unique_code (auto-generated)
├── total_clicks
├── total_signups
├── total_conversions
├── total_earnings
└── timestamps

referral_transactions
├── id (PK)
├── referral_id (FK)
├── referred_email
├── event_registration_id (FK, nullable)
├── commission_amount
├── status (enum: pending, paid)
└── timestamps

-- ====================================================
-- SITE SETTINGS
-- ====================================================
site_settings (singleton)
├── id (PK)
├── site_name
├── site_tagline
├── logo_url
├── favicon_url
├── primary_phone, secondary_phone
├── primary_email
├── address
├── social_links (json)
├── analytics_ga4_id
├── analytics_meta_pixel_id
├── default_meta_title_template (e.g. "{page} | mutuperguruantinggi.id")
├── default_meta_description
├── default_og_image_url
├── footer_text
└── updated_at

-- ====================================================
-- REDIRECTS (untuk migrasi SEO)
-- ====================================================
redirects
├── id (PK)
├── source_path (e.g. "/old-page")
├── destination_path (e.g. "/new-page")
├── status_code (301, 302)
├── hit_count
└── timestamps

-- ====================================================
-- AUDIT LOGS
-- ====================================================
audit_logs
├── id (PK)
├── user_id (FK)
├── action (e.g. "created", "updated", "deleted")
├── resource_type (e.g. "Article", "Event")
├── resource_id
├── changes (json — before/after)
├── ip_address
└── created_at
```

### 8.2 Total Tabel: 30+

---

## 9. API ENDPOINTS

### 9.1 Public REST API (untuk Frontend)

```
GET    /api/services                          → List semua layanan
GET    /api/services/[slug]                   → Detail layanan
GET    /api/services/category/[category]      → Filter by kategori

GET    /api/certification-schemes             → List semua skema
GET    /api/certification-schemes/[slug]      → Detail skema

GET    /api/events                            → List events (?category, ?month, ?status)
GET    /api/events/[slug]                     → Detail event
POST   /api/events/[id]/register              → Register ke event

GET    /api/articles                          → List artikel (?category, ?tag, ?author)
GET    /api/articles/[slug]                   → Detail artikel
GET    /api/articles/featured                 → Featured articles
POST   /api/articles/[id]/view                → Increment view count

GET    /api/experts                           → List pakar
GET    /api/experts/[slug]                    → Detail pakar

GET    /api/case-studies                      → List studi kasus
GET    /api/case-studies/[slug]               → Detail studi kasus

GET    /api/partners                          → List PT mitra
GET    /api/testimonials                      → List testimoni
GET    /api/packages                          → List paket
GET    /api/faqs                              → List FAQ (?category)
GET    /api/resources                         → List resource

POST   /api/resources/[id]/download           → Download (capture email)
POST   /api/leads                             → Submit konsultasi form
POST   /api/subscribers                       → Subscribe newsletter
POST   /api/contact                           → Form kontak

GET    /api/search?q=                         → Search global
GET    /api/sitemap                           → Sitemap JSON (untuk client-side)
```

### 9.2 Admin/CMS API (Protected)

```
POST   /api/admin/auth/login
POST   /api/admin/auth/logout
GET    /api/admin/auth/me

# CRUD untuk semua resource
GET/POST/PUT/DELETE /api/admin/services
GET/POST/PUT/DELETE /api/admin/events
GET/POST/PUT/DELETE /api/admin/articles
GET/POST/PUT/DELETE /api/admin/experts
GET/POST/PUT/DELETE /api/admin/partners
GET/POST/PUT/DELETE /api/admin/testimonials
GET/POST/PUT/DELETE /api/admin/resources
GET/POST/PUT/DELETE /api/admin/faqs

# Lead management
GET    /api/admin/leads
PUT    /api/admin/leads/[id]/status
GET    /api/admin/leads/export

# Analytics
GET    /api/admin/dashboard/stats              → Total leads, events, articles
GET    /api/admin/analytics/page-views
GET    /api/admin/analytics/conversions

# Media library
POST   /api/admin/media/upload
DELETE /api/admin/media/[id]

# Settings
GET/PUT /api/admin/settings
```

### 9.3 Webhook Endpoints

```
POST /api/webhooks/payment-callback        → Midtrans/Xendit callback
POST /api/webhooks/email-bounce            → Resend/SendGrid bounce
POST /api/webhooks/whatsapp                → WA Business API (jika integrated)
```

---

## 10. ROLES, PERMISSIONS & WORKFLOW

### 10.1 Role Matrix

| Permission | Super Admin | Admin | Editor | Author | Subscriber |
|------------|-------------|-------|--------|--------|------------|
| Manage users | ✓ | ✗ | ✗ | ✗ | ✗ |
| Manage settings | ✓ | ✗ | ✗ | ✗ | ✗ |
| Manage services | ✓ | ✓ | ✗ | ✗ | ✗ |
| Manage events | ✓ | ✓ | ✓ | ✗ | ✗ |
| Publish articles | ✓ | ✓ | ✓ | ✗ | ✗ |
| Write articles | ✓ | ✓ | ✓ | ✓ | ✗ |
| View leads | ✓ | ✓ | ✗ | ✗ | ✗ |
| Export data | ✓ | ✓ | ✗ | ✗ | ✗ |
| Comment on articles | ✓ | ✓ | ✓ | ✓ | ✓ |
| Register events | ✓ | ✓ | ✓ | ✓ | ✓ |

### 10.2 Content Workflow

```
[Author writes draft]
         │
         ▼
[Draft saved] ──→ [Author submits for review]
                              │
                              ▼
                  [Editor reviews & feedback]
                              │
                              ├─→ [Reject → back to Author]
                              │
                              └─→ [Approve & schedule/publish]
                                              │
                                              ▼
                                    [Published — live on site]
                                              │
                                              ▼
                                    [Auto-trigger:]
                                    · Sitemap update
                                    · Notify subscribers
                                    · Cache invalidation
```

---

## 11. STACK TEKNOLOGI & DEPLOYMENT

### 11.1 Frontend Stack (Next.js Recommended)

```json
{
  "framework": "Next.js 14 (App Router)",
  "ui": "Tailwind CSS + shadcn/ui",
  "icons": "Lucide React atau Tabler Icons",
  "forms": "React Hook Form + Zod",
  "state": "Zustand (client) + TanStack Query (server)",
  "animation": "Framer Motion (selective)",
  "rich_text": "Tiptap (untuk render dari CMS)",
  "image": "next/image (auto optimization)",
  "analytics": "Vercel Analytics + GA4",
  "monitoring": "Sentry",
  "testing": "Vitest + Playwright"
}
```

### 11.2 Backend Stack (Strapi Recommended)

```json
{
  "cms": "Strapi v5",
  "database": "PostgreSQL 16",
  "cache": "Redis 7",
  "search": "Meilisearch",
  "media_storage": "Cloudflare R2 atau AWS S3",
  "email": "Resend",
  "payment": "Midtrans (Indonesia)",
  "captcha": "Cloudflare Turnstile",
  "auth": "Strapi auth + JWT",
  "monitoring": "Better Stack / Uptime Robot"
}
```

### 11.3 DevOps & Deployment

| Komponen | Hosting | Estimasi Biaya/bulan |
|----------|---------|----------------------|
| Frontend (Next.js) | Vercel Pro | $20 (Rp320K) |
| CMS (Strapi) | Railway / VPS Hetzner | $15-30 (Rp240K-480K) |
| Database PostgreSQL | Railway managed atau Supabase | $10-25 (Rp160K-400K) |
| Object Storage | Cloudflare R2 (gratis 10GB) | $0-5 |
| CDN | Cloudflare Free | $0 |
| Email (Resend) | Free tier 3K/bulan | $0-20 |
| Domain | Sudah ada | - |
| Monitoring | UptimeRobot Free | $0 |
| **Total estimasi** | | **~$50-100/bulan (Rp800K-1.6jt)** |

### 11.4 CI/CD Pipeline

```
GitHub Push
    │
    ├──→ Lint + Type-check (GitHub Actions)
    │
    ├──→ Run tests (Vitest unit + Playwright E2E)
    │
    └──→ Deploy
            ├──→ Preview (per PR)
            └──→ Production (main branch)
                    │
                    └──→ Sitemap regeneration
                          + Cache purge
```

---

## 12. ROADMAP IMPLEMENTASI

### Phase 1: Foundation (Sprint 1-2, Minggu 1-4)
- [x] Blueprint approval ← *Anda ada di sini*
- [ ] Setup repo, design tokens, base components
- [ ] Setup Strapi CMS + schema database
- [ ] Setup hosting & domain
- [ ] Implement halaman: Beranda, Layanan pillar, Tentang
- [ ] SEO foundation (sitemap, robots, schema base)

### Phase 2: Content Pages (Sprint 3-4, Minggu 5-8)
- [ ] 6 halaman detail Skema Sertifikasi
- [ ] Halaman AMI Digital
- [ ] 10 halaman Mitra (SPMI, AMI, OBE, dll)
- [ ] Halaman Paket Reguler & Premium
- [ ] Halaman Pakar (listing + detail)
- [ ] Footer & navigation finalization

### Phase 3: Dynamic Content (Sprint 5-6, Minggu 9-12)
- [ ] Event system (listing, detail, registration)
- [ ] Article/Blog system (listing, detail, kategori, tag)
- [ ] Resource library (gated download)
- [ ] Studi Kasus
- [ ] Search functionality (Meilisearch)
- [ ] Newsletter subscription

### Phase 4: Interactive Tools & Optimization (Sprint 7-8, Minggu 13-16)
- [ ] Tools: Cek Status Mutu Prodi & PT
- [ ] Lead capture forms (Konsultasi Gratis)
- [ ] Payment integration (Midtrans untuk event berbayar)
- [ ] Referral program
- [ ] Admin dashboard analytics
- [ ] Performance optimization (Core Web Vitals)
- [ ] SEO audit & content seeding (20 artikel pilar)
- [ ] User acceptance testing
- [ ] **GO LIVE** 🚀

### Phase 5: Post-Launch (Bulan 5+)
- Content marketing (30+ artikel/bulan)
- A/B testing CTA conversion
- Backlink building
- Performance monitoring
- Iterasi berdasarkan analytics

---

## LAMPIRAN A: CHECKLIST PRE-LAUNCH

### SEO Checklist
- [ ] Title tag unique di setiap halaman
- [ ] Meta description di setiap halaman
- [ ] H1 unique & mengandung primary keyword
- [ ] Alt text di semua gambar
- [ ] XML sitemap submitted ke Google Search Console
- [ ] Schema markup tervalidasi (Google Rich Results Test)
- [ ] Mobile-friendly (Google Mobile-Friendly Test)
- [ ] Page speed > 90 (PageSpeed Insights)
- [ ] Canonical URL di setiap halaman
- [ ] Robots.txt benar
- [ ] 404 page custom dengan CTA back to home
- [ ] HTTPS aktif & no mixed content

### Technical Checklist
- [ ] Backup database otomatis (daily)
- [ ] SSL certificate
- [ ] CDN active
- [ ] Image lazy loading
- [ ] WebP format support
- [ ] Font preload (Manrope, Plus Jakarta Sans)
- [ ] Critical CSS inlined
- [ ] Service worker untuk offline support (opsional)

### Content Checklist
- [ ] Minimal 20 artikel pilar siap saat launch
- [ ] Semua 12 pakar punya profil lengkap
- [ ] 6 studi kasus dengan testimoni
- [ ] 6 skema sertifikasi halaman detail
- [ ] FAQ minimal 30 pertanyaan
- [ ] 5 resource lead magnet siap download

### Compliance Checklist
- [ ] Kebijakan Privasi (PDP UU 27/2022)
- [ ] Syarat & Ketentuan
- [ ] Cookie consent banner
- [ ] GDPR-ready (untuk visitor internasional)

---

## LAMPIRAN B: KEY METRICS UNTUK MONITORING

### Pre-Launch Targets (Month 3)
- 10.000 page views/bulan
- 500 newsletter subscribers
- 100 lead konsultasi/bulan
- 50 event registrations/bulan

### Year 1 Targets
- 100.000 page views/bulan
- 5.000 newsletter subscribers
- 500 lead konsultasi/bulan
- Top 3 Google ranking untuk 10 keyword utama
- Domain Authority > 30

---

*Blueprint v2.0 ini dirancang untuk skala pertumbuhan jangka panjang. Setiap section bisa diimplementasi bertahap—tidak harus sekaligus. Prioritas implementasi tergantung capacity tim & budget yang tersedia.*

**Next Step**: Setelah blueprint v2.0 ini Anda approve, saya akan lanjutkan dengan:
1. Membangun mockup HTML untuk 3-5 halaman utama tambahan (Layanan pillar, Detail skema, Event listing, Detail event, Artikel)
2. Atau mulai implementasi backend Strapi schema lengkap
3. Atau prototyping admin panel mockup

Tinggal pilih mana yang ingin diprioritaskan terlebih dahulu.
