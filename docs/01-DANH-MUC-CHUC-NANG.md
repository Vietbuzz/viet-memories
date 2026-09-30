# KÝ ỨC VIỆT — TÀI LIỆU THIẾT KẾ CHỨC NĂNG
## Phần 1: Danh mục chức năng Web & App

> Phiên bản 0.1 — Bản cơ sở để thống nhất
> Quy ước mức ưu tiên: **P0** = bắt buộc có trong MVP · **P1** = giai đoạn 2 · **P2** = giai đoạn sau
> Quy ước nền tảng: **W** = web desktop · **M** = web/PWA trên điện thoại · **N** = app native (GĐ2)

---

## A. BẢN ĐỒ HỆ THỐNG

Hệ thống chia thành **5 khu vực** với đối tượng và mục đích khác nhau:

```
┌──────────────────────────────────────────────────────────────┐
│ KV1 · CỔNG CÔNG KHAI          Không đăng nhập · Mobile-first  │
│      Trang giới thiệu · Trang tưởng niệm · Trang dòng họ      │
├──────────────────────────────────────────────────────────────┤
│ KV2 · KHÔNG GIAN GIA ĐÌNH     Đăng nhập · Mobile + Desktop    │
│      Hồ sơ của tôi · Kho tư liệu · Cây gia phả · Lời mời      │
├──────────────────────────────────────────────────────────────┤
│ KV3 · XƯỞNG BIÊN TẬP          Đăng nhập · Desktop-first       │
│      Wizard tạo hồ sơ · Duyệt đóng góp · Xem trước · Phát hành│
├──────────────────────────────────────────────────────────────┤
│ KV4 · QUẢN TRỊ VẬN HÀNH       Nội bộ · Desktop                │
│      Đơn hàng · QR · Đối tác · Đối soát · Nhật ký · Sao lưu   │
├──────────────────────────────────────────────────────────────┤
│ KV5 · NGHĨA TRANG (B2B)       Đối tác · Desktop + Mobile      │
│      Sơ đồ khu mộ · Tìm mộ · Hồ sơ mộ · Lịch chăm sóc         │
└──────────────────────────────────────────────────────────────┘
```

---

## KV1 · CỔNG CÔNG KHAI

### A1. Trang giới thiệu (Landing)
| Mã | Chức năng | Ưu tiên | Nền tảng | Mô tả |
|---|---|---|---|---|
| A1.1 | Giới thiệu giá trị & cách hoạt động | P0 | W M | "Một đời người không nên chỉ còn lại hai dòng chữ trên bia mộ" |
| A1.2 | Xem hồ sơ mẫu hoàn chỉnh | P0 | W M | Ít nhất 1 hồ sơ demo đầy đủ — công cụ bán hàng chính |
| A1.3 | Bảng gói dịch vụ & phạm vi | P0 | W M | Ghi rõ: số hồ sơ/ảnh, dung lượng, số lần sửa, thời gian giao, thời hạn lưu, hỗ trợ, quyền xuất dữ liệu |
| A1.4 | Form gửi yêu cầu tư vấn | P0 | W M | Tên, SĐT/Zalo, nhu cầu, nguồn biết đến → vào CRM |
| A1.5 | Trang dành cho đối tác | P1 | W | Chính sách, hoa hồng, cách giới thiệu |
| A1.6 | Blog / câu chuyện khách hàng | P2 | W M | SEO & tăng niềm tin |

### A2. Trang tưởng niệm công khai *(sản phẩm lõi)*
| Mã | Chức năng | Ưu tiên | Nền tảng | Mô tả |
|---|---|---|---|---|
| A2.1 | Ảnh bìa + chân dung + tên + năm sinh–mất + lời giới thiệu | P0 | M W | Khu đầu trang, tối ưu cho điện thoại dọc |
| A2.2 | Tab **Câu chuyện** | P0 | M W | Tiểu sử dạng văn, có ghi "Gia đình biên soạn" |
| A2.3 | Tab **Dấu mốc** (Dòng thời gian) | P0 | M W | Mốc năm + sự kiện + ảnh kèm |
| A2.4 | Tab **Album** | P0 | M W | Ảnh/video theo bộ sưu tập, có chú thích |
| A2.5 | Tab **Người thân** | P0 | M W | Thẻ người thân (vợ/chồng, con, cháu) + link sang hồ sơ của họ |
| A2.6 | Tab **Nơi an nghỉ** | P0 | M W | Vị trí mộ, ảnh khu mộ, ngày giỗ âm lịch, chỉ dẫn đường đi |
| A2.7 | Khối thông tin bên phải | P0 | W | Quê quán, nghề nghiệp, người quản lý hồ sơ |
| A2.8 | Nút **Chia sẻ** | P0 | M W | Link, Zalo, Facebook, sao chép |
| A2.9 | Nút **Gửi một kỷ niệm** | P0 | M W | Người ngoài gửi ảnh/lời kể → hàng chờ duyệt |
| A2.10 | Nút **Đề nghị kết nối** | P1 | M W | "Tôi là người thân" → gửi yêu cầu cấp quyền |
| A2.11 | Thanh điều hướng dưới (mobile) | P0 | M | Trang chủ · Câu chuyện · Kỷ niệm · Gia đình · Nơi an nghỉ |
| A2.12 | Nghe ghi âm / xem video ký ức | P1 | M W | Giọng kể của người thân |
| A2.13 | Sổ tưởng niệm (lời nhắn từ khách) | P1 | M W | Hiển thị sau khi gia đình duyệt |
| A2.14 | Thắp nến / dâng hoa ảo | P2 | M W | Tương tác nhẹ, tăng cảm xúc |
| A2.15 | Chế độ tưởng niệm ngày giỗ | P2 | M W | Giao diện đặc biệt vào ngày giỗ |

> **Ràng buộc hiển thị:** trang này chỉ render các trường có mức hiển thị **Công khai**. Nội dung mức Gia đình chỉ hiện khi người xem đã đăng nhập và có quyền.

### A3. Trang dòng họ công khai
| Mã | Chức năng | Ưu tiên | Nền tảng | Mô tả |
|---|---|---|---|---|
| A3.1 | Giới thiệu dòng họ, nhà thờ họ | P1 | W M | Lịch sử, tổ tiên, địa chỉ |
| A3.2 | Cây gia phả rút gọn (công khai) | P1 | W M | Chỉ tên + năm, không chi tiết |
| A3.3 | Khu mộ tổ | P1 | W M | Vị trí, ảnh |
| A3.4 | Lịch giỗ chạp chung | P2 | W M | Theo lịch âm |

---

## KV2 · KHÔNG GIAN GIA ĐÌNH *(đăng nhập)*

### B1. Tài khoản
| Mã | Chức năng | Ưu tiên | Nền tảng |
|---|---|---|---|
| B1.1 | Đăng ký / đăng nhập bằng **số điện thoại + OTP** (ưu tiên) hoặc email | P0 | W M |
| B1.2 | Quên mật khẩu / đăng nhập lại | P0 | W M |
| B1.3 | Hồ sơ cá nhân (tên, ảnh, liên hệ) | P0 | W M |
| B1.4 | Chuyển đổi giữa các "không gian" (Gia đình Nguyễn / Dòng họ X) | P0 | W M |
| B1.5 | Đăng nhập bằng Google / Zalo | P1 | W M |
| B1.6 | Bảo mật 2 lớp cho người quản lý | P1 | W |

### B2. Bảng điều khiển gia đình
| Mã | Chức năng | Ưu tiên | Nền tảng | Mô tả |
|---|---|---|---|---|
| B2.1 | Danh sách hồ sơ người thân | P0 | W M | Kèm trạng thái: Nháp / Chờ duyệt / Đã xuất bản |
| B2.2 | Việc cần làm | P0 | W M | Hồ sơ chưa hoàn tất, đóng góp chờ duyệt, lời mời chưa trả lời |
| B2.3 | Hoạt động gần đây | P1 | W M | Ai vừa gửi gì, ai vừa sửa gì |
| B2.4 | Nhắc ngày giỗ (âm lịch) | P1 | W M N | Nhắc trước 7 ngày / 1 ngày |
| B2.5 | Dung lượng & thời hạn dịch vụ | P0 | W M | Hiển thị rõ đã dùng bao nhiêu, hết hạn khi nào |

### B3. Kho tư liệu
| Mã | Chức năng | Ưu tiên | Nền tảng | Mô tả |
|---|---|---|---|---|
| B3.1 | Tải lên ảnh / video / tài liệu (kéo-thả, chọn nhiều) | P0 | W M | Có thanh tiến trình, tải lại khi lỗi |
| B3.2 | Chụp ảnh tư liệu bằng camera điện thoại | P0 | M | Chụp ảnh cũ, giấy tờ gia phả |
| B3.3 | Ghi âm lời kể trực tiếp | P1 | M N | Ghi âm người lớn tuổi kể chuyện |
| B3.4 | Gắn thẻ: ai trong ảnh, năm nào, ở đâu | P0 | W M | Cơ sở để sắp xếp dòng thời gian |
| B3.5 | Ghi nguồn gốc & quyền sử dụng | P0 | W M | Ai đóng góp, có được công khai không |
| B3.6 | Đặt mức hiển thị cho từng tư liệu | P0 | W M | Công khai / Gia đình / Riêng tư |
| B3.7 | Xem theo Ảnh / Tài liệu / Video | P0 | W M | Lọc, tìm kiếm |
| B3.8 | Giữ bản gốc + phiên bản chỉnh sửa | P0 | (hệ thống) | Không bao giờ ghi đè bản gốc |
| B3.9 | Yêu cầu dịch vụ phục hồi ảnh | P1 | W M | Chọn ảnh → đặt dịch vụ → báo giá |

### B4. Người thân & lời mời
| Mã | Chức năng | Ưu tiên | Nền tảng | Mô tả |
|---|---|---|---|---|
| B4.1 | Mời người thân qua link / SĐT / Zalo | P0 | W M | Kèm vai trò được cấp |
| B4.2 | Quản lý danh sách thành viên & quyền | P0 | W | Thêm, đổi vai trò, thu hồi |
| B4.3 | Duyệt yêu cầu "Tôi là người thân" | P1 | W M | Từ nút A2.10 |
| B4.4 | Chuyển giao quyền quản lý hồ sơ | P1 | W | Có quy trình xác minh |

### B5. Cây gia phả
| Mã | Chức năng | Ưu tiên | Nền tảng | Mô tả |
|---|---|---|---|---|
| B5.1 | Xem cây gia phả (dọc, theo thế hệ) | P1 | W M | Thu/phóng, di chuyển |
| B5.2 | Thêm người thân vào cây | P1 | W M | Cha, mẹ, vợ/chồng, con |
| B5.3 | Khai báo & xác nhận quan hệ | P1 | W M | Trạng thái: đề xuất / đã xác nhận / mâu thuẫn |
| B5.4 | Cảnh báo trùng lặp hồ sơ | P1 | (hệ thống) | Gợi ý gộp — **không tự gộp** |
| B5.5 | Tìm kiếm trong dòng họ | P1 | W M | Theo tên, đời, nhánh |
| B5.6 | Quản lý nhánh họ & phân quyền theo nhánh | P2 | W | Cho khách dòng họ |
| B5.7 | Nhập gia phả từ file (ảnh chụp / Excel) | P2 | W | Dịch vụ số hóa |
| B5.8 | Xuất gia phả (PDF / GEDCOM / Excel) | P1 | W | Cam kết "xuất dữ liệu được" |

---

## KV3 · XƯỞNG BIÊN TẬP *(đăng nhập, desktop-first)*

### C1. Wizard tạo/chỉnh sửa hồ sơ — 7 bước
| Bước | Tên | Ưu tiên | Nội dung |
|---|---|---|---|
| 1 | **Thông tin cơ bản** | P0 | Ảnh chân dung, họ tên, năm sinh, năm mất, quê quán, nghề nghiệp, lời giới thiệu ngắn, nguồn thông tin |
| 2 | **Câu chuyện cuộc đời** | P0 | Tiểu sử dạng văn + các dấu mốc theo năm |
| 3 | **Ảnh & tư liệu** | P0 | Chọn từ kho, sắp xếp album, viết chú thích |
| 4 | **Người thân** | P0 | Khai báo quan hệ, liên kết sang hồ sơ khác |
| 5 | **Nơi an nghỉ** | P0 | Nghĩa trang, khu–lô–hàng–mộ, tọa độ, ảnh, ngày giỗ âm lịch |
| 6 | **Quyền hiển thị** | P0 | Đặt mức Công khai / Gia đình / Riêng tư cho từng khối |
| 7 | **Kiểm tra & hoàn tất** | P0 | Checklist trước xuất bản + gửi gia đình duyệt |

| Mã | Chức năng hỗ trợ wizard | Ưu tiên | Mô tả |
|---|---|---|---|
| C1.1 | Tự lưu bản nháp | P0 | Hiển thị "Đã lưu bản nháp" |
| C1.2 | Quay lại bất kỳ bước nào | P0 | Không ép tuyến tính |
| C1.3 | Cho phép để trống / đánh dấu "chờ xác nhận" | P0 | Không ép nhập đủ khi chưa rõ |
| C1.4 | **Xem trước trực tiếp** (panel bên phải) | P0 | Thấy ngay trang tưởng niệm sẽ trông thế nào |
| C1.5 | Checklist trước xuất bản | P0 | ☐ Xác nhận tên và ngày tháng ☐ Kiểm tra quyền hiển thị ☐ Gia đình duyệt nội dung |
| C1.6 | Nút **Gửi gia đình duyệt** | P0 | Chuyển trạng thái → Chờ duyệt |
| C1.7 | AI gợi ý viết tiểu sử từ tư liệu | P1 | **Chỉ đề xuất**, hiển thị rõ "do AI soạn, cần duyệt" |
| C1.8 | AI gợi ý mốc thời gian từ ảnh | P2 | Từ metadata & chú thích |

### C2. Duyệt & phát hành
| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| C2.1 | Hàng chờ duyệt nội dung | P0 | Đóng góp từ người thân & khách |
| C2.2 | So sánh phiên bản (trước/sau) | P1 | Thấy rõ thay đổi gì |
| C2.3 | Duyệt / từ chối / yêu cầu sửa | P0 | Kèm lý do |
| C2.4 | Xuất bản hồ sơ | P0 | Sinh URL công khai + kích hoạt QR |
| C2.5 | Gỡ xuất bản / ẩn tạm | P1 | |
| C2.6 | Lịch sử thay đổi đầy đủ | P0 | Ai sửa, sửa gì, lúc nào, ai duyệt |
| C2.7 | Khôi phục phiên bản cũ | P1 | |

---

## KV4 · QUẢN TRỊ VẬN HÀNH *(nội bộ)*

### D1. Đơn hàng & khách hàng
| Mã | Chức năng | Ưu tiên | Vai trò |
|---|---|---|---|
| D1.1 | Danh sách lead (có nguồn) | P0 | A2, A3 |
| D1.2 | CRM đơn giản: lead → tư vấn → báo giá → chốt | P0 | A3 |
| D1.3 | Hồ sơ đơn hàng: phạm vi, giá, thời hạn, người quản lý | P0 | A3, A6 |
| D1.4 | Checklist đơn & lịch giao | P0 | A6 |
| D1.5 | Ticket hỗ trợ khách | P1 | A6 |
| D1.6 | Mẫu báo giá & email/Zalo giới thiệu | P1 | A3 |

### D2. QR vật lý
| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| D2.1 | Sinh mã QR gắn với hồ sơ | P0 | **Link ổn định, không đổi** |
| D2.2 | Quản lý loại vật liệu (mica / kim loại / khắc đá) | P0 | |
| D2.3 | Theo dõi trạng thái: đặt → sản xuất → vận chuyển → lắp đặt → nghiệm thu | P0 | |
| D2.4 | Quét thử & xác nhận QR mở đúng trang | P0 | Bắt buộc trước bàn giao |
| D2.5 | Cấp lại QR khi hỏng / mất | P1 | Giữ nguyên link cũ |
| D2.6 | Thống kê lượt quét theo hồ sơ | P1 | Đầu vào của vòng tăng trưởng |

### D3. Đối tác
| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| D3.1 | Hồ sơ đối tác & hợp đồng | P1 | Cơ sở bia mộ, đá mỹ nghệ, tang lễ |
| D3.2 | Mã giới thiệu riêng cho từng đối tác | P1 | Gắn nguồn đơn |
| D3.3 | Bảng theo dõi đơn & hoa hồng | P1 | |
| D3.4 | Đối soát & thanh toán hoa hồng | P1 | A7 |
| D3.5 | Cổng đối tác (tự xem đơn của mình) | P2 | **Không xem được dữ liệu gia đình** |

### D4. Tài chính & báo cáo
| Mã | Chức năng | Ưu tiên |
|---|---|---|
| D4.1 | Ghi thu / chi theo đơn | P0 |
| D4.2 | Đối soát công nợ & hoa hồng | P1 |
| D4.3 | Báo cáo 5 chỉ số: đơn đã thu tiền, lãi đóng góp/đơn, đối tác có đơn lặp lại, tỷ lệ giao đúng hẹn, lỗi & công hỗ trợ sau giao | P1 |
| D4.4 | Theo dõi KPI sản phẩm (tỷ lệ hoàn tất hồ sơ, lời mời, đóng góp) | P1 |

### D5. Dữ liệu & an toàn
| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| D5.1 | Nhật ký truy cập & thao tác toàn hệ thống | P0 | Ai xem gì, ai sửa gì |
| D5.2 | Sao lưu tự động + **kiểm tra khôi phục định kỳ** | P0 | Không chỉ backup, phải test restore |
| D5.3 | Xuất dữ liệu theo hồ sơ / theo gia đình | P0 | Cam kết "rời dịch vụ được" |
| D5.4 | Rà soát quyền định kỳ | P1 | A8 |
| D5.5 | Quản lý thời hạn & nhắc gia hạn | P0 | |
| D5.6 | Quy trình xóa dữ liệu theo yêu cầu | P1 | Có xác minh, có thời gian chờ |

---

## KV5 · NGHĨA TRANG B2B *(giai đoạn sau)*

| Mã | Chức năng | Ưu tiên | Nền tảng | Mô tả |
|---|---|---|---|---|
| E1.1 | Sơ đồ nghĩa trang: khu – lô – hàng – mộ | P2 | W M | Bản đồ tương tác |
| E1.2 | Hồ sơ mộ (người an nghỉ, mã mộ, tọa độ, tình trạng) | P2 | W M | |
| E1.3 | Tìm mộ theo tên / mã | P2 | W M | Cho cả người nhà đến viếng |
| E1.4 | Chỉ dẫn đường đi trong nghĩa trang | P2 | M | |
| E1.5 | Lịch & nhật ký chăm sóc mộ | P2 | W M | |
| E1.6 | Quản trị phân quyền theo khu | P2 | W | |
| E1.7 | Báo cáo cho ban quản lý | P2 | W | |
| E1.8 | Liên kết mộ ↔ trang tưởng niệm (khi gia đình đồng ý) | P2 | W | **Cần sự đồng ý của gia đình** |
| E1.9 | Cập nhật thực địa (chụp ảnh, rà soát vị trí theo đợt) | P2 | M | App cho nhân viên |

---

## B. ĐỀ XUẤT PHẠM VI MVP (chốt để làm trước)

### ✅ Có trong MVP
- KV1: A1.1–A1.4, **A2.1–A2.11** (toàn bộ trang tưởng niệm)
- KV2: B1.1–B1.4, B2.1–B2.2, B2.5, **B3.1–B3.8**, B4.1–B4.2
- KV3: **Toàn bộ wizard 7 bước C1.1–C1.6**, C2.1, C2.3, C2.4, C2.6
- KV4: D1.1–D1.4, **D2.1–D2.4**, D4.1, D5.1–D5.3, D5.5

### ⏸ Để lại giai đoạn 2
- Cây gia phả (B5.*)
- Nhắc giỗ âm lịch (B2.4)
- AI hỗ trợ biên tập (C1.7–C1.8)
- Cổng đối tác & hoa hồng (D3.*)
- Ghi âm lời kể, video ký ức

### ⏹ Giai đoạn sau
- Toàn bộ KV5 (nghĩa trang B2B)
- App native
- Sổ tưởng niệm, thắp nến ảo, đa ngôn ngữ

---

## C. YÊU CẦU PHI CHỨC NĂNG

| Nhóm | Yêu cầu |
|---|---|
| **Hiệu năng** | Trang tưởng niệm mở < 2.5s trên 4G. Ảnh lazy-load, nén nhiều kích cỡ. |
| **Khả dụng** | QR phải mở được trên mọi trình duyệt điện thoại phổ thông, **không cần cài app, không cần đăng nhập**. |
| **Độ bền link** | URL từ QR **không bao giờ đổi** — kể cả khi hồ sơ được sửa, chuyển người quản lý hay đổi gói. |
| **Khả năng tiếp cận** | Cỡ chữ lớn, tương phản cao — người dùng nhiều tuổi. Hỗ trợ phóng to hệ thống. |
| **Tôn trọng bối cảnh** | **Không quảng cáo chen vào trang tưởng niệm.** Không bán dữ liệu gia đình. Không thu phí mở khóa ký ức đã mua. |
| **Sao lưu** | Sao lưu hằng ngày, giữ bản gốc tư liệu, kiểm tra khôi phục hàng tháng. |
| **Riêng tư** | Mặc định Riêng tư. Quét QR không cấp quyền. Nhật ký truy cập đầy đủ. |
| **Xuất dữ liệu** | Gia đình luôn xuất được toàn bộ dữ liệu của mình ở định dạng mở. |

---

**Tài liệu liên quan:**
- [00 — Tổng quan & Đối tượng sử dụng](./00-TONG-QUAN-VA-DOI-TUONG-SU-DUNG.md)
- [02 — Flow chức năng chi tiết](./02-FLOW-CHUC-NANG-CHI-TIET.md)
