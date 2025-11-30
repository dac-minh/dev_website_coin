# Crypto Dashboard - Full Stack Project

Dự án dashboard phân tích crypto với frontend React + backend FastAPI.

## 📋 Yêu cầu

- **Node.js** >= 16 (cho frontend)
- **Python** >= 3.8 (cho backend)
- **PostgreSQL** (cơ sở dữ liệu)
- **pnpm** hoặc **npm** (quản lý package Node)

## 🚀 Cách chạy project

### 1️⃣ **Cài đặt Backend (FastAPI)**

```bash
cd back-end

# Tạo virtual environment
python3 -m venv .venv

# Kích hoạt virtual environment
# Trên macOS/Linux:
source .venv/bin/activate
# Trên Windows:
.venv\Scripts\activate

# Cài đặt dependencies
pip install -r requirements.txt

# Copy file .env
cp .env.example .env

# Chỉnh sửa file .env với thông tin PostgreSQL của bạn
# Ví dụ:
# DATABASE_URL=postgresql://user:password@localhost/big_data

# (Tùy chọn) Seed dữ liệu portfolio
psql -h localhost -U your_user -d big_data -f seed_portfolio.sql

# Chạy backend server
uvicorn main:app --reload --port 8888
```

Backend sẽ chạy tại: **http://localhost:8888**

### 2️⃣ **Cài đặt Frontend (React + Vite)**

Mở **terminal mới** (giữ backend đang chạy):

```bash
cd front-end

# Cài đặt dependencies
pnpm install
# Hoặc: npm install

# Chạy development server
pnpm dev
# Hoặc: npm run dev
```

Frontend sẽ chạy tại: **http://localhost:8080**

## 📊 API Endpoints

Backend cung cấp các endpoint chính:

| Endpoint | Method | Mô tả |
|----------|--------|-------|
| `/api/coins/top100` | GET | Lấy top 100 coin theo market cap |
| `/api/coins/sparklines` | GET | Lấy dữ liệu sparkline 7 ngày |
| `/api/coin/{coin_id}/detail` | GET | Chi tiết coin |
| `/api/coin/{coin_id}/chart` | GET | Dữ liệu biểu đồ coin |
| `/api/market/cap_growth` | GET | % thay đổi market cap 24h |
| `/api/market/uptrend` | GET | Coin tăng giá mạnh nhất |
| `/api/news` | GET | Tin tức crypto |
| `/api/sentiment` | GET | Market sentiment score |

## 🏗️ Cấu trúc Project

```
FRONT-END/
├── front-end/              # React SPA
│   ├── client/
│   │   ├── pages/          # Các trang chính
│   │   ├── components/     # UI components
│   │   ├── layouts/        # Layout wrapper
│   │   └── App.tsx         # Router setup
│   ├── server/             # Express server (dev)
│   ├── vite.config.ts      # Vite config
│   └── package.json
│
└── back-end/               # FastAPI backend
    ├── main.py             # Entry point
    ├── models.py           # Pydantic models
    ├── queries.py          # SQL queries
    ├── db.py               # Database connection
    └── requirements.txt
```

## 🛠️ Các lệnh hữu ích

### Frontend

```bash
cd front-end

pnpm dev          # Chạy dev server
pnpm build        # Build production
pnpm preview      # Preview build
pnpm typecheck    # Kiểm tra TypeScript
pnpm test         # Chạy unit tests
```

### Backend

```bash
cd back-end

# Kích hoạt venv trước
source .venv/bin/activate

uvicorn main:app --reload --port 8888   # Chạy server
python -m pytest                         # Chạy tests
```

## 🔧 Cấu hình môi trường

### Backend (.env)

```env
DATABASE_URL=postgresql://user:password@localhost/big_data
DEBUG=True
PORT=8888
```

### Frontend (.env)

```env
VITE_API_BASE_URL=http://localhost:8888
```

## 📁 Cơ sở dữ liệu

Chắc chắn PostgreSQL đã chạy và có database `big_data`:

```bash
# Tạo database (nếu chưa có)
createdb -U your_user big_data

# Chạy schema (nếu cần)
psql -U your_user -d big_data < warehouse.sql
```

## 🌐 Truy cập ứng dụng

Sau khi cả frontend và backend đang chạy:

- **Frontend**: http://localhost:8080
- **Backend API**: http://localhost:8888
- **API Docs** (Swagger): http://localhost:8888/docs

## ⚙️ Troubleshooting

**Lỗi: `Failed to connect to backend`**
- Kiểm tra backend có đang chạy ở port 8888
- Kiểm tra file `.env` trong `back-end/`

**Lỗi: `ModuleNotFoundError` (Python)**
- Kiểm tra virtual environment đã kích hoạt: `source .venv/bin/activate`
- Cài đặt lại dependencies: `pip install -r requirements.txt`

**Lỗi: `Database connection failed`**
- Kiểm tra PostgreSQL có đang chạy
- Kiểm tra credentials trong `.env`

## 📝 Ghi chú

- Frontend hot reload được bật - chỉnh sửa file sẽ reload tự động
- Backend reload được bật - chỉnh sửa Python code sẽ reload tự động
- Dữ liệu được lấy từ PostgreSQL warehouse, không phải hardcode

## 📚 Tài liệu thêm

- [React Router Docs](https://reactrouter.com/)
- [FastAPI Docs](https://fastapi.tiangolo.com/)
- [TailwindCSS Docs](https://tailwindcss.com/)
- [Vite Docs](https://vitejs.dev/)

---

**Happy coding! 🚀**
