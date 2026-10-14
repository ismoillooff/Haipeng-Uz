# ⚛️ Haipeng Frontend

**Haipeng.uz internet-do'koni, administrator paneli va CRM interfeysi**

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)
![Zustand](https://img.shields.io/badge/State-Zustand-443E38)

## 📖 Vazifasi

Frontend uchta asosiy tajribani bitta React SPA ichida birlashtiradi:

1. Mijozlar uchun ommaviy internet-do'kon.
2. Mahsulot, kategoriya, buyurtma va sayt kontenti uchun admin panel.
3. Ishlab chiqarish, ombor, ishchilar, filiallar va moliya uchun CRM interfeysi.

## 🧰 Stack

| Texnologiya | Vazifasi |
| --- | --- |
| React 19 | UI komponentlari |
| TypeScript 5.9 | Statik tiplash |
| Vite 7 | Development va production build |
| React Router 7 | SPA routing |
| Zustand 5 | Auth, savat, theme va CRM state |
| Framer Motion 12 | Sahifa va komponent animatsiyalari |
| Recharts 3 | Dashboard grafiklari |
| Lucide React | Ikonkalar |

## 🚀 Ishga Tushirish

```powershell
npm install
npm run dev
```

Development manzili odatda `http://localhost:5173`.

## ⌨️ Skriptlar

| Buyruq | Vazifasi |
| --- | --- |
| `npm run dev` | Vite development server |
| `npm run build` | TypeScript tekshiruvi va production build |
| `npm run lint` | ESLint tekshiruvi |
| `npm run preview` | `dist/` buildni lokal ko'rish |

## 🗂️ Tuzilma

```text
src/
├── components/          # Public va admin komponentlari
│   └── Admin/           # Admin layout va CRM UI qismlari
├── data/
│   ├── categories.ts    # Fallback kategoriyalar
│   ├── products.ts      # Fallback mahsulotlar
│   └── mockData.ts      # CRM demo data
├── pages/
│   ├── Admin/           # Admin va CRM sahifalari
│   └── *.tsx            # Ommaviy sahifalar
├── store/
│   ├── authStore.ts     # JWT auth persistence
│   ├── cartStore.ts     # Savat
│   ├── crmStore.ts      # CRM in-memory amallari
│   └── themeStore.ts    # Theme
├── types/               # TypeScript modellar
├── api.ts               # FastAPI klienti
├── App.tsx              # Route xaritasi
└── main.tsx             # BrowserRouter bootstrap
```

## 🧭 Route'lar

| Guruh | Route'lar |
| --- | --- |
| Public | `/`, `/catalog`, `/product/:id`, `/cart`, `/checkout`, `/about`, `/contact` |
| Admin | `/panel`, `/panel/products`, `/panel/categories`, `/panel/orders`, `/panel/users`, `/panel/sliders`, `/panel/settings` |
| CRM | `/panel/crm`, `production`, `motos`, `workers`, `inventory`, `shops`, `finance`, `transactions`, `sales`, `analytics`, `settings` |

`ProtectedRoute` autentifikatsiyasiz foydalanuvchini `/panel/login` sahifasiga yo'naltiradi. `/admin` route'i `/panel`ga redirect qiladi.

## 🔌 Backend Ulanishi

`src/api.ts` quyidagi funksiyalarni beradi:

- auth login va `/me`;
- product va category CRUD;
- order yaratish, ro'yxat va status;
- userlar va dashboard;
- single/multiple upload;
- slider CRUD;
- Telegram sozlash va test.

API base URL hozir source code ichida `https://api.haipeng.uz/api` qilib yozilgan. Lokal backend uchun `http://127.0.0.1:8000/api` kerak. Keyingi refaktorda `VITE_API_URL` ishlatish tavsiya etiladi.

## 🔐 Auth Holati

`authStore` Zustand `persist` middleware orqali token va userni `localStorage`dagi `auth-storage` kalitida saqlaydi. API klient har bir himoyalangan so'rovga Bearer token qo'shadi.

Production uchun XSS xavfini kamaytirish maqsadida HttpOnly/Secure cookie asosidagi autentifikatsiyani baholash tavsiya etiladi.

## 🏭 CRM Holati

CRM ekranlari `mockData.ts` va `crmStore.ts` bilan ishlaydi. Quyidagi client-side amallar mavjud:

- motosikl qo'shish, yangilash, tugatish va sotish;
- ehtiyot qismlar va ombor harakatlari;
- ishchi, vazifa, to'lov, bonus va jarima;
- do'kon, qarz to'lovi va filialga savdo;
- mijoz, order va payment holati;
- daromad, xarajat, tranzaksiya va statistika.

> [!IMPORTANT]
> `crmStore` persist qilinmagan va FastAPI endpointlariga ulanmagan. Sahifa yangilanganda foydalanuvchi kiritgan CRM o'zgarishlari yo'qoladi. Ushbu qism hozir demo/prototip holatida.

## 🎨 Theme Va Animatsiya

Theme qiymati `themeStore` orqali boshqariladi va `document.documentElement`dagi `data-theme` atributiga yoziladi. Framer Motion route almashinuvi va UI animatsiyalarida ishlatiladi. Admin route'larda public navbar, footer va cart drawer ko'rsatilmaydi.

## ✅ Build Va Tekshiruv

```powershell
npm run lint
npm run build
npm run preview
```

Manual checklist:

- [ ] Public route'lar ochiladi.
- [ ] Katalog filter va qidiruv ishlaydi.
- [ ] Mahsulot savatga qo'shiladi.
- [ ] Checkout backendga buyurtma yuboradi.
- [ ] Login xato va muvaffaqiyatli holatlari ishlaydi.
- [ ] Himoyalangan route login talab qiladi.
- [ ] Mahsulot va kategoriya CRUD ishlaydi.
- [ ] Slider va upload ishlaydi.
- [ ] CRM sahifalari console xatosiz ochiladi.
- [ ] Desktop va mobil layout tekshiriladi.

## 🌐 Production Build

```bash
npm ci
npm run lint
npm run build
```

Natija `dist/` ichida yaratiladi. React Router SPA bo'lgani uchun nginx fallback talab qilinadi:

```nginx
location / {
    try_files $uri $uri/ /index.html;
}
```

`index.html`ni uzoq cache qilmang; hash'langan `/assets/` fayllarini uzoq cache qilish mumkin.

## 🔐 Xavfsizlik

- frontendga JWT secret, Telegram token yoki boshqa server secretini yozmang;
- `VITE_` prefiksli qiymatlar browser bundle ichiga tushishini unutmang;
- backenddan kelgan matn va URLlarni xavfsiz render qiling;
- admin tokenini XSSdan himoyalash uchun CSP va cookie strategiyasini ko'rib chiqing;
- checkout inputlarini faqat frontendga ishonmay, backendda ham tekshiring;
- production API faqat HTTPS orqali ishlasin.

## 🧯 Muammolar

| Muammo | Yechim |
| --- | --- |
| API so'rovi ishlamaydi | `src/api.ts` URL, backend va CORS |
| Login saqlanmaydi | Browser localStorage va `auth-storage` |
| Admin 401 qaytaradi | Token mavjudligi va muddati |
| Upload rasmi ochilmaydi | API host va qaytgan file URL |
| CRM data yo'qoladi | Hozir persist/backend integratsiyasi mavjud emas |
| Refreshda 404 | Serverga SPA fallback qo'shing |
| TypeScript build xatosi | `npm run build`dagi birinchi xatoni tuzating |
| CSS eski ko'rinadi | Browser cache va yangi `dist/assets` hashlarini tekshiring |

## 🧩 Keyingi Bosqichlar

- [ ] `VITE_API_URL` konfiguratsiyasi;
- [ ] CRM backend endpointlari va persistence;
- [ ] API response'lar uchun qat'iy TypeScript turlari, `any`ni kamaytirish;
- [ ] loading, empty va error state'larni standartlashtirish;
- [ ] accessibility va keyboard navigation testi;
- [ ] component/unit testlar;
- [ ] Playwright end-to-end testlar;
- [ ] production error monitoring.

To'liq arxitektura, deploy, xavfsizlik, GitHub va aloqa ma'lumotlari uchun [asosiy README](../README.md)ni o'qing.
