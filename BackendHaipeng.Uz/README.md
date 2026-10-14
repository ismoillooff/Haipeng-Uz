# ⚡ Haipeng Backend

**Haipeng.uz internet-do'koni va administrator paneli uchun FastAPI REST API**

![FastAPI](https://img.shields.io/badge/FastAPI-0.115-009688?logo=fastapi&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?logo=python&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-2.0-D71F00?logo=sqlalchemy&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-Development-003B57?logo=sqlite&logoColor=white)

## 📖 Vazifasi

Backend mahsulotlar, kategoriyalar, buyurtmalar, foydalanuvchilar, hero sliderlar, rasmlar va Telegram sozlamalarini boshqaradi. Public katalog endpointlari autentifikatsiyasiz ishlaydi; o'zgartirish amallari JWT Bearer token va `admin` roli bilan himoyalangan.

## 🧰 Stack

| Paket | Versiya/vazifa |
| --- | --- |
| FastAPI | `0.115.0`, API framework |
| Uvicorn | `0.30.0`, ASGI server |
| SQLAlchemy | `2.0.35`, ORM |
| Pydantic | `2.9.0`, request validatsiyasi |
| python-jose | JWT |
| passlib + bcrypt | Parol hash |
| python-multipart | File upload |
| httpx | Telegram API; `requirements.txt`ga qo'shilishi kerak |

## 🚀 Ishga Tushirish

```powershell
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

## ⌨️ CLI Buyruqlari

| Buyruq | Vazifasi |
| --- | --- |
| `python main.py runserver` | Development server, port `8000` |
| `python main.py createsuperuser` | Interaktiv admin yaratish |
| `python main.py resetdb` | Lokal bazani o'chirib, qayta seed qilish |

> [!CAUTION]
> `resetdb` barcha lokal ma'lumotlarni qaytarib bo'lmaydigan tarzda o'chiradi. Productionda ishlatmang.

## 🗂️ Tuzilma

```text
BackendHaipeng.Uz/
├── routers/           # Endpoint modullari
├── auth.py            # JWT, hash va admin_required
├── database.py        # SQLite engine va SessionLocal
├── main.py            # FastAPI app, CORS, CLI
├── models.py          # SQLAlchemy modellar
├── schemas.py         # Pydantic sxemalar
├── seed.py            # Demo admin, user, kategoriya, mahsulot, slider
├── telegram.py        # Buyurtma xabarnomasi
├── requirements.txt
└── README.md
```

## 🔌 Endpointlar

| Guruh | Public | Admin |
| --- | --- | --- |
| Auth | `POST /api/auth/login` | `GET /api/auth/me` |
| Products | `GET /api/products`, `GET /api/products/{id}` | create, update, delete |
| Categories | list va detail | create, update, delete |
| Orders | `POST /api/orders` | list, detail, status update |
| Users | — | list, detail, delete |
| Dashboard | — | `GET /api/dashboard/stats` |
| Upload | file download | single/multiple upload |
| Slides | active slides | all, create, update, delete |
| Settings | — | Telegram get, save, test |

Swagger UI endpointlarning to'liq request va response sxemalarini ko'rsatadi.

## 🔐 Autentifikatsiya

Login javobi `access_token` va user ma'lumotlarini qaytaradi. Himoyalangan so'rovlar quyidagi header bilan yuboriladi:

```http
Authorization: Bearer YOUR_JWT_TOKEN
```

JWT muddati hozir `30 kun`. `admin_required` tokenni tekshiradi, userni database'dan topadi va `role == "admin"` shartini talab qiladi.

## 🗄️ Database

Development bazasi `haipeng.db`. Startup vaqtida `Base.metadata.create_all()` jadvallarni yaratadi, `seed_database()` esa bo'sh bazani boshlang'ich ma'lumotlar bilan to'ldiradi.

| Model | Muhim maydonlar |
| --- | --- |
| `User` | username, password hash, role, kontakt, savdo statistikasi |
| `Category` | slug, nomlar, izoh, rasm |
| `Product` | narx, kategoriya, rasmlar, specs, qoldiq, rating |
| `Order` | mijoz, yetkazish, to'lov, status, itemlar, jami |
| `HeroSlide` | matn, rasm, CTA, rang, tartib, faollik |
| `SiteSetting` | Telegram token va channel ID kabi key/value |

SQLite va runtime uploadlar `.gitignore` orqali Git'dan chiqarilgan. Production uchun PostgreSQL va Alembic migration tizimi tavsiya etiladi.

## 📤 Upload

Ruxsat etilgan formatlar: `.jpg`, `.jpeg`, `.png`, `.webp`, `.gif`, `.svg`.

Maksimal hajm: `10 MB` har bir fayl uchun. Fayllar random nom bilan `routers/uploads/` ichiga yoziladi.

Hozir validatsiya extension va hajm bilan cheklangan. Productionda MIME, real image decoding, SVG sanitizatsiya va path traversal himoyasini kuchaytirish kerak.

## 📲 Telegram

`site_settings` jadvalida bot token va kanal ID saqlanadi. Buyurtma yaratilganda `BackgroundTasks` orqali kanalga HTML formatdagi xabar yuboriladi. Telegram sozlanmagan bo'lsa buyurtma baribir yaratiladi, xabarnoma o'tkazib yuboriladi.

## ✅ Tekshiruv

```powershell
python -m compileall .
python main.py runserver
```

```powershell
Invoke-RestMethod http://127.0.0.1:8000/health
Invoke-RestMethod http://127.0.0.1:8000/api/products
Invoke-RestMethod http://127.0.0.1:8000/api/categories
```

Hozir avtomatlashtirilgan testlar yo'q. Auth, CRUD, checkout, upload, Telegram va permission testlarini qo'shish tavsiya etiladi.

## 🔐 Production Xavfsizligi

Public repository yoki production deploydan oldin:

- JWT secretni koddan environment variable'ga ko'chiring;
- seed admin credentiallarini olib tashlang va almashtiring;
- Telegram tokenini API response'da maskalang;
- CORS'ni aniq HTTPS originlar bilan cheklang;
- login va checkout uchun rate limiting qo'shing;
- upload kontentini real format bo'yicha tekshiring;
- HTTPS, security headers, audit log va monitoring sozlang;
- PostgreSQL, migration va backup strategiyasiga o'ting.

> [!WARNING]
> Secret Git tarixiga tushgan bo'lsa, faylni o'chirish yoki `.gitignore` yetarli emas. Credentialni darhol almashtirish kerak.

## 🌐 Production

Reloadsiz Uvicorn yoki Gunicorn/Uvicorn worker, systemd va nginx reverse proxy tavsiya etiladi:

```bash
.venv/bin/uvicorn main:app --host 127.0.0.1 --port 8000
```

Nginx upload limitini backenddagi 10 MB dan biroz yuqori, masalan `11M`, qilib sozlang. Database va `routers/uploads/` uchun muntazam backup yarating.

## 🧯 Muammolar

| Muammo | Yechim |
| --- | --- |
| `httpx` topilmadi | `pip install httpx` va keyin dependency ro'yxatini yangilang |
| CORS xatosi | Frontend originini `main.py` ro'yxatiga qo'shing |
| `401` | Bearer token mavjudligi va muddati |
| `403` | User roli `admin` bo'lishi kerak |
| SQLite locked | Parallel yozuvni kamaytiring yoki PostgreSQLga o'ting |
| Telegram xabari yo'q | Token, channel ID, bot admin huquqi va tarmoq |
| Upload 400 | Extension va 10 MB limitni tekshiring |

To'liq loyiha, deploy, GitHub va aloqa ma'lumotlari uchun [asosiy README](../README.md)ni o'qing.
