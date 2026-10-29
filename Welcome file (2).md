-   **Báo cáo phân tích (I/O):** Mô tả luồng dữ liệu từ lúc nhấn Ctrl+S đến khi xuất hiện tích xanh trên file.
  
   [Nhấn Ctrl+S] 
	│ 
	▼
[1. Ghi Local SSD] ──► Hệ điều hành ghi thẳng file .js vào ổ cứng (Tốc độ tối đa, không có độ trễ mạng).
	│
	 ▼
 [2. Git Engine Kiểm tra] ──► Git nhận diện thay đổi file, bỏ qua hoàn toàn node_modules (nhờ .gitignore). 
	 │ 
	 ▼ 
 [3. Cloud Sync Daemon Quét] ──► Tiến trình đồng bộ nền kiểm tra thay đổi, loại trừ các file/thư mục nằm trong danh sách chặn (Exclusion List). 
	│ 
	▼
 [4. Đẩy gói tin tối ưu lên Cloud] ──► Chỉ các tệp mã nguồn thay đổi (dung lượng vài KB) được mã hóa và đồng bộ lên đám mây. 
	 │
	  ▼
  [5. Xác nhận & Tích xanh] ──► Cloud trả về trạng thái hoàn tất, biểu tượng tích xanh xuất hiện; tính năng "Files On-Demand" tự động giải phóng bộ nhớ đệm cục bộ nếu cần.
-   **Thiết kế:** Sơ đồ tổ chức thư mục Cloud chuẩn cho một lập trình viên (bao gồm phân loại: Code, Docs, Assets).
D:\Project\SmartFood\
│
├── .gitignore              # Chứa các quy tắc chặn node_modules, .env, dist/, build/
├── package.json            # Bản đồ khai báo thư viện (QUAN TRỌNG: Thay thế cho node_modules)
├── package-lock.json       # Khóa phiên bản thư viện chính xác
│
├── src/                    # [CODE] Mã nguồn chính của ứng dụng JavaScript
│   ├── controllers/        # Xây dựng logic điều hướng
│   ├── models/             # Định nghĩa cấu trúc cơ sở dữ liệu
│   └── app.js              # Điểm khởi chạy ứng dụng (Entry point)
│
├── docs/                   # [DOCS] Tài liệu kỹ thuật dự án
│   ├── api-specs.md        # Tài liệu mô tả API
│   └── architecture.md     # Sơ đồ kiến trúc hệ thống (RACI, WBD...)
│
├── assets/                 # [ASSETS] Tài nguyên đồ họa, hình ảnh giao diện, UI/UX
│   ├── images/             # Ảnh minh họa món ăn, logo Startup
│   └── wireframes/         # Bản vẽ thiết kế giao diện thô
│
└── node_modules/           # [LOCAL ONLY] Thư mục thư viện phụ thuộc (ĐÃ BỊ LOẠI TRỪ KHỎI CLOUD & GIT)
