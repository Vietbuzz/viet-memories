# Ký Ức Việt — Bộ tài liệu thiết kế chức năng

Bản **v0.2** (05/10/2026): tổng hợp từ 15 tài liệu/infographic chiến lược, đã nhập ý kiến cộng tác viên.
Mục đích: để hai founder **thống nhất phạm vi** trước khi sang thiết kế UI/UX và kiến trúc kỹ thuật.

## Bản thiết kế

Nằm trong [`overview/`](./overview/). Đây là bản đang dùng.

| Tài liệu | Nội dung |
|---|---|
| [00 — Tổng quan & Đối tượng sử dụng](./overview/00-TONG-QUAN-VA-DOI-TUONG-SU-DUNG.md) | Sản phẩm, nền tảng, 4 mảng kinh doanh, đối tượng, quyền, mức hiển thị, mô hình dữ liệu, cam kết lưu trữ, quyết định đã chốt và điểm còn mở |
| [01 — Danh mục chức năng](./overview/01-DANH-MUC-CHUC-NANG.md) | 5 khu vực, gói Basic và mua thêm, tạo hồ sơ nhanh, thanh toán, bảng QR, mức ưu tiên P0/P1/P2, phạm vi MVP theo từng mã |
| [02 — Flow chức năng chi tiết](./overview/02-FLOW-CHUC-NANG-CHI-TIET.md) | Hành trình tự mua, tạo nhanh, kích hoạt, giao bảng, đối tác bia mộ; trạng thái nội dung, thanh toán, hiển thị và sản xuất tách riêng |

## Ý kiến cộng tác viên

Nằm trong [`suggestions/`](./suggestions/). Đã nhập vào bản v0.2. Giữ lại để đối chiếu nguồn quyết định.

| Tài liệu | Nội dung |
|---|---|
| [00 — Góp ý](./suggestions/00-gop-y.md) | Sửa các mục đã chốt (gói tính theo hồ sơ, thanh toán một lần, vòng đời bản nháp, vật liệu QR, hoa hồng đối tác); bổ sung tạo hồ sơ nhanh, mua gói & giao hàng, dịch vụ biên tập ký ức; làm rõ gia phả, quyền riêng tư, kế thừa; đồng bộ mức ưu tiên P0/P1/P2 và các flow F4, F7, F10–F15 |
| [01 — Bổ sung](./suggestions/01-bo-sung.md) | Gói Basic dưới 100.000đ/hồ sơ (tối đa 5 ảnh), nâng dung lượng, dịch vụ video tính riêng, bảng QR (mica, kim loại, gốm) là tùy chọn; chức năng nâng gói trên hồ sơ hiện có; hành trình mua: bản nháp → xem trước → chọn gói → tùy chọn bảng/dịch vụ → thanh toán → kích hoạt |

## Nguồn tài liệu gốc

| File ảnh | Nội dung chính đã khai thác |
|---|---|
| `01_Giao_dien_web_tren_dien_thoai.png` | Mockup 5 màn hình mobile: Trang chủ, Câu chuyện, Kỷ niệm, Gia đình, Nơi an nghỉ |
| `03_Infographic_tong_quan_chi_tiet.png` | Bài toán, giải pháp, trải nghiệm, MVP, mô hình doanh thu, quyền riêng tư, vòng tăng trưởng, KPI |
| `04_Bon_mang_kinh_doanh_cot_loi.png` | 4 mảng: Tưởng niệm&QR, Gia phả&Dòng họ, Nội dung&Kho ký ức, Nghĩa trang&Vị trí mộ |
| `05_Lo_trinh_phat_trien_bon_mang.png` | Thứ tự phát triển & điều kiện đi tiếp từng mảng |
| `06_Dinh_vi_va_khach_hang.png` | 4 nhóm khách hàng + vai trò người mua/góp/duyệt |
| `07_Tinh_huong_va_hanh_trinh_khach_hang.png` | 3 tình huống sử dụng + hành trình khách hàng 6 bước + 3 nguyên tắc trải nghiệm |
| `08_Goi_dich_vu_va_website_dau_tien.png` | 4 gói dịch vụ + 6 trang website MVP |
| `09_Du_lieu_quyen_quan_ly_va_niem_tin.png` | 5 thực thể dữ liệu, 3 mức hiển thị, ai được làm gì, cam kết duy trì |
| `10_Tim_khach_ban_hang_va_ban_giao.png` | Kênh bán, bộ công cụ, lead→đơn, quy trình 7 bước một đơn |
| `11_Hieu_qua_kinh_doanh_va_thu_nghiem_90_ngay.png` | Chi phí, 3 câu hỏi hiệu quả, lộ trình 90 ngày, 5 chỉ số |
| `12_So_do_tu_duy_tong_quan.png` | Mindmap 12 nhánh toàn dự án |
| `13_So_do_phong_ban_AI.png` | 8 vai trò A1–A8, phân công, nhịp điều hành |
| `20_Concept_trang_tuong_niem_may_tinh.png` | Mockup trang tưởng niệm desktop (5 tab) |
| `21_Concept_chinh_sua_ho_so_may_tinh.png` | Mockup wizard chỉnh sửa hồ sơ 7 bước + panel xem trước |
| `Ảnh Codex 18_06_21...png` | Bản đồ nguồn thu chi tiết 6 nhóm |

## Bước tiếp theo đề xuất

1. Chốt các điểm còn mở ở mục 11 tài liệu 00: số ngày lưu bản nháp, dung lượng mỗi ảnh và giới hạn tiểu sử Basic, giá các gói nâng cấp, mẫu bảng gốm.
2. Sang thiết kế **wireframe/UI** cho các màn hình ở Phụ lục B tài liệu 02, gồm tạo nhanh, chọn gói, thanh toán và theo dõi đơn.
3. Song song: thiết kế **lược đồ CSDL** và **kiến trúc kỹ thuật**, với bốn trạng thái tách riêng.
