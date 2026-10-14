# 🏍️ Haipeng CRM

**Haipeng.uz uchun internet-do'kon, administrator paneli va ishlab chiqarish CRM platformasi**

Katalog · Savat · Buyurtmalar · Admin panel · Ishlab chiqarish · Ombor · Moliya · Telegram

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.115-009688?logo=fastapi&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?logo=python&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-Development-003B57?logo=sqlite&logoColor=white)

**[MyWeb](https://myweb.uz) × [Nyrosoft](https://nyrosoft.uz)**

---

## 📖 Loyiha Haqida

**Haipeng CRM** — `haipeng.uz` uchun yaratilgan full-stack savdo va boshqaruv platformasi. Loyiha bitta interfeys ichida ommaviy mototexnika internet-do'koni, administrator boshqaruvi va korxonaning ichki CRM jarayonlarini birlashtiradi.

Frontend mijozlarga mahsulotlarni ko'rish, katalogni filtrlash, savat tuzish va buyurtma yuborish imkonini beradi. Administrator paneli mahsulotlar, kategoriyalar, buyurtmalar, mijozlar, sliderlar, rasmlar va Telegram xabarnomalarini boshqaradi. CRM interfeysi ishlab chiqarish, motosikllar, ehtiyot qismlar, ishchilar, filiallar, savdo va moliyani nazorat qilish uchun mo'ljallangan.

| Qism | Papka | Stack | Vazifasi |
| --- | --- | --- | --- |
| Backend | `BackendHaipeng.Uz/` | FastAPI, SQLAlchemy, SQLite, JWT | Do'kon va admin API, autentifikatsiya, upload, Telegram |
| Frontend | `FrontHaipeng.uz/` | React 19, TypeScript, Vite, Zustand | Ommaviy sayt, admin panel va CRM interfeysi |

**Hujjat holati:** README loyiha kodlari, route'lar, API endpointlari, database modellari va frontend store'lari bevosita tekshirilgan holda yozildi.

> [!IMPORTANT]
> Do'kon va klassik admin modullari FastAPI backend bilan ishlaydi. CRM ma'lumotlari hozircha `src/data/mockData.ts` va `src/store/crmStore.ts` ichidagi xotira holatida ishlaydi. CRM o'zgarishlari backendga yozilmaydi va sahifa yangilanganda boshlang'ich mock holatiga qaytadi.

## 🧭 Mundarija

- [Imkoniyatlar](#-imkoniyatlar)
- [Texnologiyalar](#-texnologiyalar)
- [Arxitektura](#️-arxitektura)
- [Loyiha tuzilmasi](#️-loyiha-tuzilmasi)
- [Talablar](#-talablar)
- [Lokal o'rnatish](#-lokal-ornatish)
- [Frontend route'lari](#-frontend-routelari)
- [API endpointlari](#-api-endpointlari)
- [Database](#️-database)
- [Telegram integratsiyasi](#-telegram-integratsiyasi)
- [Build va tekshiruv](#-build-va-tekshiruv)
- [Production deploy](#-production-deploy)
- [Xavfsizlik](#-production-xavfsizligi)
- [Git va GitHub](#-git-va-github)
- [Backup](#-backup-va-texnik-xizmat)
- [Muammolar va yechimlar](#-muammolar-va-yechimlar)
- [Roadmap](#-rivojlantirish-roadmap)
- [Mualliflar va aloqa](#-mualliflar-va-aloqa)
- [Foydalanish huquqlari](#-foydalanish-huquqlari)

## ✨ Imkoniyatlar

| Yo'nalish | Holat | Tavsif |
| --- | --- | --- |
| 🛍️ Internet-do'kon | Ishlaydi | Bosh sahifa, katalog, mahsulot tafsilotlari va qidiruv |
| 🛒 Savat va checkout | Ishlaydi | Savat boshqaruvi, yetkazish va buyurtma yuborish |
| 🔐 Administrator paneli | Ishlaydi | JWT login va himoyalangan `/panel` route'lari |
| 🏍️ Mahsulotlar | Ishlaydi | CRUD, narx, rasm, xususiyat, rang, reyting va qoldiq holati |
| 🗂️ Kategoriyalar | Ishlaydi | CRUD va kategoriyadagi mahsulotlar soni |
| 📦 Buyurtmalar | Ishlaydi | Yaratish, ro'yxat, tafsilot va status boshqaruvi |
| 👥 Foydalanuvchilar | Ishlaydi | Qidiruv, statistika va oddiy foydalanuvchini o'chirish |
| 🖼️ Sliderlar | Ishlaydi | Faol/nofaol hero sliderlar va tartiblash |
| 📤 Media upload | Ishlaydi | Bitta yoki bir nechta rasm yuklash, 10 MB limit |
| 📲 Telegram | Ishlaydi | Yangi buyurtmani kanalga yuborish va test xabari |
| 📊 Admin dashboard | Ishlaydi | Savdo, buyurtma, foydalanuvchi va mahsulot statistikasi |
| 🏭 CRM ishlab chiqarish | Demo holat | Motosikl yig'ish va ishlab chiqarish jarayonlari |
| 🧰 CRM ombor | Demo holat | Ehtiyot qismlar, qoldiq va kirim-chiqim |
| 👷 CRM ishchilar | Demo holat | Vazifa, oylik, avans, bonus, jarima va tarix |
| 🏪 CRM filiallar | Demo holat | Do'kon profili, savdo va qarzdorlik |
| 💰 CRM moliya | Demo holat | Tranzaksiya, daromad, xarajat, foyda va analitika |

`Demo holat` CRM interfeysi mavjudligini, ammo ma'lumotlar hali server database'iga saqlanmasligini anglatadi.

## 🧰 Texnologiyalar

| Qatlam | Texnologiyalar |
| --- | --- |
| Frontend | React 19, TypeScript 5.9, Vite 7, React Router 7 |
| State va UI | Zustand, Framer Motion, Recharts, Lucide React |
| Backend | Python, FastAPI 0.115, Uvicorn 0.30, Pydantic 2.9 |
| Data va auth | SQLAlchemy 2, SQLite, python-jose, passlib, bcrypt |
| Integratsiya | httpx va Telegram Bot API |

> [!NOTE]
> `httpx` backend kodida import qilingan, ammo hozirgi `requirements.txt` ichida alohida ko'rsatilmagan. Toza muhitda `pip install httpx` talab qilinishi mumkin.

## 🏗️ Arxitektura

```text
Mijoz brauzeri
      |
      v
React + Vite SPA (haipeng.uz)
      |  HTTPS / JSON / Bearer JWT
      v
FastAPI (api.haipeng.uz)
      |
      +---- SQLAlchemy ----> SQLite (development)
      +---- Uploads -------> routers/uploads/
      `---- httpx ---------> Telegram Bot API
```

```text
Login -> POST /api/auth/login -> JWT -> localStorage (auth-storage)
      -> Authorization: Bearer <token> -> admin_required
```

## 🗂️ Loyiha Tuzilmasi

```text
Haipeng Crm/
├── BackendHaipeng.Uz/
│   ├── routers/
│   │   ├── auth.py          # Login va /me
│   │   ├── products.py      # Mahsulotlar CRUD
│   │   ├── categories.py    # Kategoriyalar CRUD
│   │   ├── orders.py        # Checkout va buyurtmalar
│   │   ├── users.py         # Foydalanuvchilar
│   │   ├── dashboard.py     # Admin statistika
│   │   ├── slides.py        # Hero sliderlar
│   │   ├── upload.py        # Rasm yuklash
│   │   └── settings.py      # Telegram sozlamalari
│   ├── auth.py              # JWT va admin guard
│   ├── database.py          # SQLAlchemy engine/session
│   ├── main.py              # FastAPI app va CLI
│   ├── models.py            # Database modellari
│   ├── schemas.py           # Pydantic sxemalari
│   ├── seed.py              # Boshlang'ich demo data
│   ├── telegram.py          # Buyurtma xabarnomasi
│   └── requirements.txt
├── FrontHaipeng.uz/
│   ├── public/              # Statik fayllar
│   ├── src/components/      # Do'kon va admin UI
│   ├── src/data/            # Katalog va CRM mock data
│   ├── src/pages/           # Public, admin va CRM sahifalar
│   ├── src/store/           # Zustand store'lar
│   ├── src/types/           # TypeScript interfeyslar
│   ├── src/api.ts           # Backend API klienti
│   ├── src/App.tsx          # Route xaritasi
│   └── package.json
├── .gitignore
└── README.md
```

## 📋 Talablar

| Komponent | Talab |
| --- | --- |
| Python | 3.11 yoki yangi |
| Node.js | 20 LTS yoki yangi |
| npm | Zamonaviy versiya |
| Git | Repository bilan ishlash uchun |
| Brauzer | Chrome, Edge, Firefox yoki Safari |
| Production | Linux VPS, nginx va HTTPS tavsiya etiladi |

```powershell
python --version
node --version
npm --version
git --version
```

## 🚀 Lokal O'rnatish

### 1. Repositoryni olish

```powershell
git clone <REPOSITORY_URL>
cd "Haipeng Crm"
```

`<REPOSITORY_URL>` o'rniga loyihaning haqiqiy GitHub manzilini kiriting.

### 2. Backend

```powershell
cd BackendHaipeng.Uz
py -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
pip install httpx
python main.py runserver
```

| Manzil | Vazifasi |
| --- | --- |
| `http://127.0.0.1:8000/` | API holati |
| `http://127.0.0.1:8000/health` | Health check |
| `http://127.0.0.1:8000/docs` | Swagger UI |
| `http://127.0.0.1:8000/redoc` | ReDoc |

Birinchi startup vaqtida SQLAlchemy jadvallarni yaratadi va bo'sh bazaga demo ma'lumotlarini seed qiladi.

```powershell
# Yangi administrator
python main.py createsuperuser

# Development bazasini qayta yaratish
python main.py resetdb
```

> [!CAUTION]
> `resetdb` mavjud `haipeng.db` va barcha lokal ma'lumotlarni o'chiradi. Production serverda ishlatmang.

### 3. Frontend

Yangi PowerShell oynasida:

```powershell
cd FrontHaipeng.uz
npm install
npm run dev
```

Frontend odatda `http://localhost:5173` manzilida ishlaydi.

### 4. Lokal API URL

Hozir `src/api.ts` ichida production API hardcode qilingan:

```ts
const API_BASE = 'https://api.haipeng.uz/api';
```

Lokal backend uchun vaqtincha `http://127.0.0.1:8000/api` qiymatidan foydalaning. Keyingi refaktorda `VITE_API_URL` environment variable joriy qilish tavsiya etiladi; bu imkoniyat hozirgi kodda hali mavjud emas.

## 🧭 Frontend Route'lari

### Ommaviy sahifalar

| Route | Sahifa |
| --- | --- |
| `/` | Bosh sahifa |
| `/catalog` | Mahsulot katalogi |
| `/product/:id` | Mahsulot tafsilotlari |
| `/cart` | Savat |
| `/checkout` | Buyurtma rasmiylashtirish |
| `/about` | Kompaniya haqida |
| `/contact` | Aloqa |

### Admin va CRM

| Route | Bo'lim |
| --- | --- |
| `/panel/login` | Administrator kirishi |
| `/panel` yoki `/panel/dashboard` | Dashboard |
| `/panel/products` | Mahsulotlar |
| `/panel/categories` | Kategoriyalar |
| `/panel/orders` | Buyurtmalar |
| `/panel/users` | Foydalanuvchilar |
| `/panel/sliders` | Hero sliderlar |
| `/panel/settings` | Telegram sozlamalari |
| `/panel/crm` | CRM dashboard |
| `/panel/crm/production` | Ishlab chiqarish |
| `/panel/crm/motos` | Motosikllar |
| `/panel/crm/workers` | Ishchilar |
| `/panel/crm/workers/:id` | Ishchi profili |
| `/panel/crm/inventory` | Ombor |
| `/panel/crm/shops` | Do'konlar |
| `/panel/crm/shops/:id` | Do'kon profili |
| `/panel/crm/finance` | Moliya |
| `/panel/crm/finance/new` | Yangi tranzaksiya |
| `/panel/crm/finance/:id` | Tranzaksiya tafsiloti |
| `/panel/crm/transactions` | Tranzaksiyalar |
| `/panel/crm/sales` | Savdo |
| `/panel/crm/analytics` | Analitika |
| `/panel/crm/settings` | CRM sozlamalari |

`/admin` va `/admin/*` avtomatik ravishda `/panel`ga yo'naltiriladi.

## 🔌 API Endpointlari

| Method va endpoint | Ruxsat | Vazifasi |
| --- | --- | --- |
| `POST /api/auth/login` | Public | Login va JWT olish |
| `GET /api/auth/me` | Admin | Joriy admin profili |
| `GET /api/products` | Public | Filterlangan mahsulotlar |
| `GET /api/products/{id}` | Public | Mahsulot va o'xshashlar |
| `POST/PUT/DELETE /api/products...` | Admin | Mahsulot CRUD |
| `GET /api/categories...` | Public | Kategoriyalar |
| `POST/PUT/DELETE /api/categories...` | Admin | Kategoriya CRUD |
| `POST /api/orders` | Public | Checkout buyurtmasi |
| `GET /api/orders...` | Admin | Buyurtmalar va tafsilot |
| `PUT /api/orders/{id}/status` | Admin | Status yangilash |
| `GET/DELETE /api/users...` | Admin | Foydalanuvchilar |
| `GET /api/dashboard/stats` | Admin | Dashboard statistikasi |
| `POST /api/upload` | Admin | Bitta rasm yuklash |
| `POST /api/upload/multiple` | Admin | Bir nechta rasm |
| `GET /api/upload/files/{name}` | Public | Yuklangan fayl |
| `GET /api/slides` | Public | Faol sliderlar |
| `GET /api/slides/all` | Admin | Barcha sliderlar |
| `POST/PUT/DELETE /api/slides...` | Admin | Slider CRUD |
| `/api/settings/telegram...` | Admin | Telegram sozlash va test |

Mahsulot filtrlari: `category`, `search`, `sort`, `in_stock`, `min_price`, `max_price`, `limit`, `offset`, `featured`.

Buyurtma statuslari: `pending`, `paid`, `delivered`, `cancelled`.

Upload formatlari: `.jpg`, `.jpeg`, `.png`, `.webp`, `.gif`, `.svg`; har bir fayl uchun limit `10 MB`.

To'liq interaktiv sxema: `http://127.0.0.1:8000/docs`.

## 🗄️ Database

Development bazasi: `BackendHaipeng.Uz/haipeng.db`.

| Jadval | Vazifasi |
| --- | --- |
| `users` | Admin va checkout orqali yaratilgan mijozlar |
| `categories` | Mahsulot kategoriyalari |
| `products` | Mahsulot, narx, media va xususiyatlar |
| `orders` | Buyurtma, mijoz, itemlar va status |
| `hero_slides` | Bosh sahifa sliderlari |
| `site_settings` | Telegram bot tokeni va channel ID |

Database `.gitignore` orqali Git'dan chiqarilgan. Migration tizimi hozir mavjud emas; jadvallar `Base.metadata.create_all()` orqali yaratiladi.

> [!WARNING]
> SQLite faylini GitHubga yuklamang. Unda mijoz telefonlari, buyurtmalar, admin hash'i va Telegram sozlamalari bo'lishi mumkin.

## 📲 Telegram Integratsiyasi

Admin panel orqali bot token va kanal ID database'ga saqlanadi. Yangi buyurtma yaratilganda backend background task orqali kanalga buyurtma raqami, mijoz, telefon, yetkazish, mahsulotlar, summa va vaqtni yuboradi.

1. BotFather orqali bot yarating.
2. Botni guruh yoki kanalga administrator qiling.
3. Admin panelda token va channel ID kiriting.
4. Test xabarini yuboring.
5. Test buyurtma orqali notificationni tekshiring.

Bot tokenni log, screenshot yoki GitHub README ichiga yozmang.

## ✅ Build Va Tekshiruv

Frontend:

```powershell
cd FrontHaipeng.uz
npm run lint
npm run build
npm run preview
```

Backend smoke check:

```powershell
cd BackendHaipeng.Uz
.venv\Scripts\Activate.ps1
python -m compileall .
python main.py runserver
```

Boshqa terminalda:

```powershell
Invoke-RestMethod http://127.0.0.1:8000/health
Invoke-RestMethod http://127.0.0.1:8000/api/products
Invoke-RestMethod http://127.0.0.1:8000/api/categories
```

Production oldidan checklist:

- [ ] Frontend lint va build xatosiz tugaydi.
- [ ] Backend `/health` `ok` qaytaradi.
- [ ] Public katalog va kategoriya endpointlari ishlaydi.
- [ ] Login va himoyalangan endpointlar tekshiriladi.
- [ ] Mahsulot, kategoriya va slider CRUD ishlaydi.
- [ ] Checkout buyurtma yaratadi.
- [ ] Telegram xabarnomasi yuboriladi.
- [ ] Upload turi va 10 MB limit tekshiriladi.
- [ ] SPA deep-link refresh 404 bermaydi.
- [ ] Mobil va desktop interfeys tekshiriladi.

Hozir avtomatlashtirilgan backend yoki end-to-end testlar yo'q. Yuqoridagilar manual smoke test hisoblanadi.

## 🌐 Production Deploy

```text
haipeng.uz      -> nginx -> FrontHaipeng.uz/dist
api.haipeng.uz  -> nginx -> Uvicorn/Gunicorn -> FastAPI -> database
```

Frontend build:

```bash
cd FrontHaipeng.uz
npm ci
npm run lint
npm run build
```

Nginx SPA namunasi:

```nginx
server {
    listen 443 ssl http2;
    server_name haipeng.uz www.haipeng.uz;
    root /srv/haipeng/FrontHaipeng.uz/dist;
    index index.html;

    location /assets/ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

Backend systemd namunasi:

```ini
[Unit]
Description=Haipeng FastAPI
After=network.target

[Service]
User=deploy
WorkingDirectory=/srv/haipeng/BackendHaipeng.Uz
ExecStart=/srv/haipeng/BackendHaipeng.Uz/.venv/bin/uvicorn main:app --host 127.0.0.1 --port 8000
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

API nginx proxy:

```nginx
location / {
    proxy_pass http://127.0.0.1:8000;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
    client_max_body_size 11M;
}
```

Server user'i, yo'llar, SSL sertifikatlari va domenlarni o'z muhitingizga moslang.

## 🔐 Production Xavfsizligi

> [!CAUTION]
> JWT secret va boshlang'ich admin credentiallari hozir source code ichida mavjud. Public GitHubga yuborishdan oldin ularni environment variables'ga ko'chiring va mavjud qiymatlarni almashtiring.

1. JWT secretni kamida 32 baytli tasodifiy qiymat bilan almashtiring.
2. Seed admin login/parolini source code'dan olib tashlang.
3. Telegram tokenini plaintext API response orqali qaytarmang.
4. Login va checkout endpointlariga rate limiting qo'shing.
5. CORS'da faqat aniq HTTPS originlarni qoldiring.
6. SVG uploadni taqiqlang yoki sanitizatsiya qiling.
7. Extension bilan birga MIME va rasm kontentini tekshiring.
8. JWT uchun HttpOnly cookie strategiyasini baholang.
9. PostgreSQL, migration va transactionlardan foydalaning.
10. HTTPS, security header, monitoring va audit loglarni sozlang.

Secret avval GitHubga yuborilgan bo'lsa, `.gitignore` yetarli emas: credentialni almashtiring va kerak bo'lsa Git tarixini tozalang.

## 🌿 Git Va GitHub

Repository yaratishdan oldin ignore qoidalarini tekshiring:

```powershell
git status
git check-ignore -v BackendHaipeng.Uz\haipeng.db
git check-ignore -v BackendHaipeng.Uz\routers\uploads\example.png
git check-ignore -v FrontHaipeng.uz\node_modules\react\index.js
```

Yangi repository uchun:

```powershell
git init
git branch -M main
git add .
git status --short
git diff --cached --stat
git diff --cached --check
git commit -m "Haipeng CRM loyihasi"
git remote add origin <REPOSITORY_URL>
git push -u origin main
```

`git add .` dan keyin staged fayllarni tekshiring. `haipeng.db`, `.env`, `routers/uploads/`, `node_modules/`, `.venv`, `__pycache__`, `dist` va loglar staged bo'lmasligi kerak.

## 💾 Backup Va Texnik Xizmat

SQLite backup olishdan oldin backendga yozuvlar kelishini vaqtincha to'xtating:

```powershell
Copy-Item BackendHaipeng.Uz\haipeng.db D:\Backups\haipeng-$(Get-Date -Format yyyy-MM-dd-HHmm).db
```

- database va uploadlarni muntazam backup qiling;
- backupni serverdan alohida joyda saqlang;
- secretlarni shifrlangan holda saqlang;
- tiklashni test muhitida sinang;
- disk, upload va loglarni monitoring qiling;
- dependencylarni reja asosida yangilang.

Kattaroq production yuklamasi uchun PostgreSQL va uning native backup vositalariga o'tish tavsiya etiladi.

## 🧯 Muammolar Va Yechimlar

| Muammo | Tekshirish va yechim |
| --- | --- |
| Frontend backendga ulanmaydi | `src/api.ts` API URL, backend porti va CORS |
| `ModuleNotFoundError: httpx` | Virtual environment ichida `pip install httpx` |
| Login ishlamaydi | Database seed, admin hisob va `/api/auth/login` |
| Admin route login sahifasiga qaytadi | `auth-storage` tokeni va JWT muddati |
| `401 Token kerak` | `Authorization: Bearer <token>` headeri |
| `403 Admin huquqi kerak` | User roli `admin` ekanligi |
| Buyurtma Telegramga bormaydi | Bot token, channel ID, bot huquqi va internet |
| Upload 400 qaytaradi | Extension va 10 MB limit |
| Database lock xatosi | Parallel SQLite yozuvlari; PostgreSQLni ko'rib chiqing |
| SPA route refreshda 404 | nginx `try_files ... /index.html` fallback |
| CRM o'zgarishi yo'qoladi | CRM hozir mock/in-memory |
| Build TypeScript xatosi beradi | Birinchi type errorni tuzatib qayta build qiling |

```bash
journalctl -u haipeng-api -n 100 --no-pager
tail -n 100 /var/log/nginx/error.log
```

## 🧩 Rivojlantirish Roadmap

Quyidagilar mavjud funksiya emas, keyingi rivojlantirish uchun tavsiyalar:

- [ ] CRM uchun FastAPI modellari, endpointlari va persistence;
- [ ] Alembic migration tizimi;
- [ ] PostgreSQL production konfiguratsiyasi;
- [ ] `.env` va `VITE_API_URL` konfiguratsiyasi;
- [ ] JWT secret va seed credentiallarni environmentga ko'chirish;
- [ ] owner/admin/manager/omborchi/hisobchi rollari;
- [ ] backend unit va integration testlari;
- [ ] Playwright end-to-end testlari;
- [ ] audit log va admin amallari tarixi;
- [ ] Telegram tokenini shifrlash yoki secret storage;
- [ ] upload content validation va object storage;
- [ ] monitoring, structured logs va alertlar;
- [ ] avtomatik backup va restore testi;
- [ ] CI/CD pipeline.

## 👨‍💻 Mualliflar Va Aloqa

Ushbu loyiha **MyWeb** hamda **Nyrosoft** tomonidan ishlab chiqilgan.

| Aloqa | Ma'lumot |
| --- | --- |
| Dasturchi | Hayotbek Ismoilov |
| Telefon / WhatsApp | `+998 95 005 15 45` |
| Telegram | [@ismoillooff](https://t.me/ismoillooff) |
| Instagram | [@ismoillooff](https://instagram.com/ismoillooff) |
| LinkedIn | [ismoillooff](https://www.linkedin.com/in/ismoillooff/) |
| MyWeb | [myweb.uz](https://myweb.uz) |
| Nyrosoft | [nyrosoft.uz](https://nyrosoft.uz) |

Loyihani o'rnatish, productionga chiqarish, CRM backendini yaratish, Telegram integratsiyasi yoki texnik yordam bo'yicha ishlab chiquvchi bilan bog'laning.

## 📄 Foydalanish Huquqlari

Repositoryda alohida `LICENSE` fayli mavjud bo'lmasa, kodni ommaviy ko'rish uning nusxasini olish, qayta tarqatish yoki tijoriy ishlatishga avtomatik ruxsat bermaydi. Foydalanish va moslashtirish huquqlari uchun loyiha egasi bilan bog'laning.

---

**Haipeng CRM · Savdo va ishlab chiqarish boshqaruv platformasi**

**[MyWeb](https://myweb.uz) × [Nyrosoft](https://nyrosoft.uz) · Hayotbek Ismoilov**
