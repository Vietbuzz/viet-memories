# KÝ ỨC VIỆT — TÀI LIỆU THIẾT KẾ CHỨC NĂNG
## Phần 1: Danh mục chức năng Web & App

> Phiên bản 0.2 — Đã nhập ý kiến cộng tác viên (05/10/2026)
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
│      Hồ sơ của tôi · Kho tư liệu · Mua gói · Lời mời          │
├──────────────────────────────────────────────────────────────┤
│ KV3 · XƯỞNG BIÊN TẬP          Đăng nhập · Desktop-first       │
│      Tạo nhanh · Chỉnh sửa nâng cao · Duyệt · Kích hoạt       │
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
| A1.3 | Bảng gói dịch vụ & phạm vi | P0 | W M | Tính phí theo từng hồ sơ người đã khuất. Một tài khoản quản lý nhiều hồ sơ. Chi tiết bảng giá ngay dưới |
| A1.4 | Form gửi yêu cầu tư vấn | P0 | W M | Tên, SĐT/Zalo, nhu cầu, nguồn biết đến → vào CRM |
| A1.5 | Trang dành cho đối tác | P1 | W | Cách giới thiệu. Đối tác bia mộ: công ty thu phí nền tảng và cấp QR; đối tác tự báo giá, thu tiền khắc đá. Hoa hồng chỉ khi có thỏa thuận riêng |
| A1.6 | Blog / câu chuyện khách hàng | P2 | W M | SEO & tăng niềm tin |

**A1.3 — Gói dịch vụ (đã chốt hướng, một số con số còn mở):**

| Thành phần | Nội dung |
|---|---|
| **Basic — dưới 100.000đ/hồ sơ** | Một hồ sơ người đã khuất; tối đa **5 ảnh** và tiểu sử; trình bày theo mẫu; đường dẫn chia sẻ và mã QR số; thanh toán một lần; lưu trữ trọn đời theo phạm vi gói |
| **Nâng cấp dung lượng** | Mở rộng số ảnh, dung lượng tư liệu, âm thanh và video theo từng gói. Giá và giới hạn cụ thể chốt sau |
| **Dịch vụ làm video** | Tính phí riêng theo phạm vi biên tập, thời lượng và số lần chỉnh sửa. Công bố dung lượng lưu video đi kèm. Mua thêm không tạo hồ sơ mới |
| **Bảng QR vật lý** | Tùy chọn, không bắt buộc. Mica, kim loại hoặc gốm. Giá bảng và phí vận chuyển hiện riêng |

Năm ảnh Basic tính cả ảnh chân dung và ảnh bìa nếu là hai tệp khác nhau. Cần chốt thêm dung lượng tối đa mỗi ảnh và giới hạn tiểu sử. "5 ảnh" không có nghĩa là dung lượng không giới hạn.

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
| A3.2 | Cây gia phả rút gọn (công khai) | P1 | W M | Chỉ tên + năm của người đã khuất mà gia đình chọn công khai. Dữ liệu người còn sống không mặc định công khai |
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
| B2.1 | Danh sách hồ sơ người thân | P0 | W M | Trạng thái nội dung: Nháp / Chờ duyệt / Đã kích hoạt / Tạm ẩn. Tách khỏi thanh toán, quyền hiển thị và đơn sản xuất |
| B2.2 | Việc cần làm | P0 | W M | Hồ sơ chưa hoàn tất, bản nháp sắp hết hạn, đóng góp chờ duyệt, lời mời chưa trả lời |
| B2.3 | Hoạt động gần đây | P1 | W M | Ai vừa gửi gì, ai vừa sửa gì |
| B2.4 | Nhắc ngày giỗ (âm lịch) | P1 | W M N | Nhắc trước 7 ngày / 1 ngày |
| B2.5 | Gói hồ sơ & dung lượng | P0 | W M | Gói đã mua, trạng thái thanh toán, số ảnh và dung lượng đã dùng, quyền lợi. Không hiện ngày hết hạn cho hồ sơ đã mua |

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
| B4.4 | Người quản lý dự phòng & tiếp quản | P0 | W | Mỗi hồ sơ khai người dự phòng. Tiếp quản có xác minh; MVP xử lý thủ công được |

### B5. Cây gia phả

Thêm người vào cây **không tự phát sinh phí**. Thành viên gia phả tối giản (tên, năm, quan hệ) khác với hồ sơ tưởng niệm trả phí. Nâng một thành viên tối giản thành hồ sơ tưởng niệm là một bước mua gói riêng (B6).

| Mã | Chức năng | Ưu tiên | Nền tảng | Mô tả |
|---|---|---|---|---|
| B5.1 | Xem cây gia phả (dọc, theo thế hệ) | P1 | W M | Thu/phóng, di chuyển |
| B5.2 | Thêm người thân vào cây | P1 | W M | Cha, mẹ, vợ/chồng, con. Không tạo đơn hàng |
| B5.3 | Khai báo & xác nhận quan hệ | P1 | W M | Trạng thái: đề xuất / đã xác nhận / mâu thuẫn |
| B5.4 | Cảnh báo trùng lặp hồ sơ | P1 | (hệ thống) | Gợi ý gộp — **không tự gộp** |
| B5.5 | Tìm kiếm trong dòng họ | P1 | W M | Theo tên, đời, nhánh |
| B5.6 | Quản lý nhánh họ & phân quyền theo nhánh | P2 | W | Cho khách dòng họ |
| B5.7 | Nhập gia phả từ file (ảnh chụp / Excel) | P2 | W | Dịch vụ số hóa |
| B5.8 | Xuất gia phả (PDF / GEDCOM / Excel) | P1 | W | Cam kết "xuất dữ liệu được" |

### B6. Mua gói, thanh toán & giao hàng *(P0)*

Bảng QR và dịch vụ video là tùy chọn. Khách có thể bắt đầu với Basic, rồi mua bảng, nâng dung lượng hoặc đặt video trên **đúng hồ sơ đó**.

| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| B6.1 | Chọn gói cho hồ sơ | P0 | Basic hoặc gói dung lượng cao hơn. Không gói sẵn bảng vào mọi hồ sơ |
| B6.2 | Nâng gói trên hồ sơ hiện có | P0 | Khi đạt giới hạn: thay tư liệu hoặc nâng gói. Giữ nội dung, đường dẫn và QR. Hiện quyền lợi tăng thêm và số tiền phải trả trước khi thanh toán |
| B6.3 | Tùy chọn bảng QR | P0 | Vật liệu, màu, kích thước, nội dung trên bảng, phụ kiện. Giá bảng và phí vận chuyển tách khỏi phí nền tảng. Có lối QR số phối hợp đối tác bia mộ, không bắt công ty khắc đá |
| B6.4 | Duyệt mẫu bảng | P0 | Khách xác nhận tên, ngày tháng, bố cục trước khi sản xuất |
| B6.5 | Thanh toán | P0 | Tạo đơn, xác nhận tiền, trạng thái chờ / lỗi / thành công. Chống tạo đơn hoặc đưa vào sản xuất trùng. Đơn thành công ghi sang D1 |
| B6.6 | Địa chỉ nhận hàng | P0 | Người nhận, số điện thoại, địa chỉ, phí giao, thời gian dự kiến. Chỉ khi có hàng vật lý |
| B6.7 | Theo dõi đơn | P0 | Khách xem tiến độ sản xuất và vận chuyển của bảng đã mua |
| B6.8 | Hỗ trợ sau giao | P0 | Báo giao hỏng, sai nội dung, QR khó quét. Yêu cầu xử lý hoặc làm lại theo chính sách |

---

## KV3 · XƯỞNG BIÊN TẬP *(đăng nhập, desktop-first)*

### C1. Tạo và chỉnh sửa hồ sơ

Hai lối vào. Khách được xem trước sau lối tạo nhanh; không bắt hoàn thành cả bảy nhóm nội dung mới được xem bản mẫu.

| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| C1.9 | Tạo nhanh | P0 | Thông tin cơ bản → tải ảnh và câu chuyện → xem trước |
| C1.10 | Tự trình bày theo mẫu | P0 | Tự bố trí ảnh, tiểu sử, dấu mốc và album; ẩn các mục trống; hiển thị đẹp trên máy tính và điện thoại |
| C1.11 | Chỉnh sửa nâng cao | P0 | Bảy nhóm nội dung bên dưới. Dùng khi khách muốn bổ sung, không phải cổng chặn xem trước |
| C1.12 | Vòng đời bản nháp | P0 | Số ngày lưu, thời điểm bắt đầu tính, nhắc trước hạn, cách xử lý khi hết hạn. **Số ngày chưa chốt** |
| C1.13 | Giữ nội dung sau thanh toán | P0 | Bản nháp trở thành hồ sơ lưu theo gói; nội dung khách đã nhập được giữ nguyên |

#### Chỉnh sửa nâng cao — 7 nhóm nội dung
| Bước | Tên | Ưu tiên | Nội dung |
|---|---|---|---|
| 1 | **Thông tin cơ bản** | P0 | Ảnh chân dung, họ tên, năm sinh, năm mất, quê quán, nghề nghiệp, lời giới thiệu ngắn, nguồn thông tin |
| 2 | **Câu chuyện cuộc đời** | P0 | Tiểu sử dạng văn + các dấu mốc theo năm |
| 3 | **Ảnh & tư liệu** | P0 | Chọn từ kho, sắp xếp album, viết chú thích |
| 4 | **Người thân** | P0 | Khai báo quan hệ hoặc tạo thành viên tối giản. Không tự phát sinh phí |
| 5 | **Nơi an nghỉ** | P0 | Nghĩa trang, khu–lô–hàng–mộ, tọa độ, ảnh, ngày giỗ âm lịch |
| 6 | **Quyền hiển thị** | P0 | Mặc định Riêng tư. Người quản lý chủ động chọn phần Công khai hoặc Gia đình |
| 7 | **Kiểm tra & hoàn tất** | P0 | Checklist trước xuất bản + gửi gia đình duyệt |

| Mã | Chức năng hỗ trợ wizard | Ưu tiên | Mô tả |
|---|---|---|---|
| C1.1 | Tự lưu bản nháp | P0 | Hiển thị "Đã lưu bản nháp" |
| C1.2 | Quay lại bất kỳ bước nào | P0 | Không ép tuyến tính |
| C1.3 | Cho phép để trống / đánh dấu "chờ xác nhận" | P0 | Không ép nhập đủ khi chưa rõ |
| C1.4 | **Xem trước trực tiếp** (panel bên phải) | P0 | Thấy ngay trang tưởng niệm sẽ trông thế nào |
| C1.5 | Checklist trước khi gửi duyệt | P0 | ☐ Xác nhận tên và ngày tháng ☐ Kiểm tra quyền hiển thị ☐ Chủ hồ sơ duyệt nội dung. Thanh toán là cổng riêng ở C2.4 |
| C1.6 | Nút **Gửi gia đình duyệt** | P0 | Chuyển trạng thái → Chờ duyệt |
| C1.7 | AI gợi ý viết tiểu sử từ tư liệu | P1 | **Chỉ đề xuất**, hiển thị rõ "do AI soạn, cần duyệt" |
| C1.8 | AI gợi ý mốc thời gian từ ảnh | P2 | Từ metadata & chú thích |

### C2. Duyệt & phát hành
| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| C2.1 | Hàng chờ duyệt nội dung | P0 | Đóng góp từ người thân & khách |
| C2.2 | So sánh phiên bản (trước/sau) | P1 | Thấy rõ thay đổi gì |
| C2.3 | Duyệt / từ chối / yêu cầu sửa | P0 | Kèm lý do |
| C2.4 | Kích hoạt hồ sơ | P0 | Chỉ khi đã xác nhận thanh toán, chủ hồ sơ đã duyệt nội dung và đã xác nhận quyền hiển thị. Sinh URL ổn định và QR số. Hồ sơ trả phí có thể giữ riêng tư |
| C2.5 | Tạm ẩn | P0 | Ẩn khỏi trang công khai. Không mất dữ liệu, không mất quyền lưu trữ đã mua, không đổi URL |
| C2.6 | Lịch sử thay đổi đầy đủ | P0 | Ai sửa, sửa gì, lúc nào, ai duyệt |
| C2.7 | Khôi phục phiên bản cũ | P1 | |

### C3. Dịch vụ biên tập ký ức *(P1 — giai đoạn đầu làm thủ công được)*

QR luôn trỏ về hồ sơ trên nền tảng. Bản video lưu trên hồ sơ độc lập với bản đăng YouTube.

| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| C3.1 | Đặt dịch vụ | P1 | Viết tiểu sử, phục hồi ảnh, biên tập video cuộc đời. Gửi tư liệu và yêu cầu; nhận báo giá |
| C3.2 | Duyệt biên tập | P1 | Duyệt kịch bản, xem bản dựng, yêu cầu sửa, duyệt bản cuối. Theo dõi tiến độ, số vòng sửa và bàn giao |
| C3.3 | Bàn giao video | P1 | Lưu video vào hồ sơ; khách tải được bản cuối. Công bố dung lượng lưu video đi kèm gói dịch vụ |
| C3.4 | Quyền sử dụng ngoài hồ sơ | P1 | Xin phép riêng nếu đăng YouTube hoặc dùng để quảng bá. Lưu phạm vi đồng ý, phiên bản được duyệt và yêu cầu gỡ |

---

## KV4 · QUẢN TRỊ VẬN HÀNH *(nội bộ)*

### D1. Đơn hàng & khách hàng
| Mã | Chức năng | Ưu tiên | Vai trò |
|---|---|---|---|
| D1.1 | Danh sách lead (có nguồn) | P0 | A2, A3 |
| D1.2 | CRM đơn giản: lead → tư vấn → báo giá → chốt | P0 | A3 |
| D1.3 | Hồ sơ đơn hàng: phạm vi gói, giá, trạng thái thanh toán, người quản lý | P0 | A3, A6 |
| D1.4 | Checklist đơn & lịch giao | P0 | A6 |
| D1.5 | Ticket hỗ trợ khách | P1 | A6 |
| D1.6 | Mẫu báo giá & email/Zalo giới thiệu | P1 | A3 |

### D2. QR vật lý
| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| D2.1 | Sinh mã QR gắn với hồ sơ | P0 | Link ổn định, không đổi khi sửa nội dung, nâng gói hoặc chuyển quản lý. Không tái sử dụng mã hồ sơ đã xóa |
| D2.2 | Loại bảng QR | P0 | **Mica** (trong nhà). **Kim loại cao cấp** (trong nhà hoặc bia mộ; màu vàng, bạc, đồng, trắng sáng). **Gốm** (chưa mở bán đến khi chốt mẫu, cách chế tác và điều kiện dùng). Không có sản phẩm công ty khắc trực tiếp lên đá |
| D2.3 | Trạng thái sản xuất bảng | P0 | Chờ duyệt mẫu → Đang sản xuất → Kiểm tra QR → Đóng gói → Vận chuyển → Đã giao. Giao bảng khoan sẵn và phụ kiện phù hợp; khách tự lắp |
| D2.4 | Kiểm tra QR trước khi giao | P0 | Quét thử, mở đúng trang. Với gốm: thêm kiểm tra khả năng quét, đóng gói chống vỡ và xử lý hư hỏng khi giao. Không áp cách khoan, bắt vít của kim loại cho gốm |
| D2.5 | Cấp lại QR khi hỏng / mất | P1 | Giữ nguyên link cũ |
| D2.6 | Thống kê lượt quét theo hồ sơ | P1 | Đầu vào của vòng tăng trưởng |

### D3. Đối tác
| Mã | Chức năng | Ưu tiên | Mô tả |
|---|---|---|---|
| D3.1 | Hồ sơ đối tác & hợp đồng | P1 | Cơ sở bia mộ, đá mỹ nghệ, tang lễ |
| D3.2 | Mã giới thiệu riêng cho từng đối tác | P1 | Gắn nguồn đơn |
| D3.3 | Theo dõi đơn đối tác | P1 | Đối tác bia mộ: không mặc định trả thêm hoa hồng. Công ty thu phí nền tảng và cấp QR; đối tác tự báo giá, thu tiền khắc đá |
| D3.4 | Đối soát hoa hồng khi có thỏa thuận | P1 | A7. Chỉ áp dụng cho thỏa thuận riêng, không áp mặc định cho đối tác bia mộ |
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
| D5.5 | Quản lý vòng đời bản nháp | P0 | Thời hạn dùng thử, nhắc trước hạn, xử lý bản nháp chưa thanh toán. Không gia hạn định kỳ cho hồ sơ đã mua |
| D5.6 | Tiếp nhận yêu cầu xóa dữ liệu | P0 | Có xác minh. MVP tiếp nhận và xử lý thủ công; quy trình xóa tự động làm sau |

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

## B. PHẠM VI MVP

Liệt kê đúng mã làm trong MVP. Không gom dải nếu trong dải có mục P1 hoặc P2.

### Có trong MVP (P0)
- **KV1:** A1.1, A1.2, A1.3, A1.4, A2.1, A2.2, A2.3, A2.4, A2.5, A2.6, A2.7, A2.8, A2.9, A2.11
- **KV2:** B1.1, B1.2, B1.3, B1.4, B2.1, B2.2, B2.5, B3.1, B3.2, B3.4, B3.5, B3.6, B3.7, B3.8, B4.1, B4.2, B4.4, B6.1–B6.8
- **KV3:** C1.1–C1.6, C1.9–C1.13, C2.1, C2.3, C2.4, C2.5, C2.6
- **KV4:** D1.1–D1.4, D2.1–D2.4, D4.1, D5.1, D5.2, D5.3, D5.5, D5.6

Gốm có mặt trong mô hình D2.2 nhưng chưa mở bán cho đến khi kiểm tra sản phẩm thật.

### Giai đoạn 2 (P1)
- A1.5, A2.10, A2.12, A2.13, A3.1–A3.3
- B1.5, B1.6, B2.3, B2.4, B3.3, B3.9, B4.3, B5.1–B5.5, B5.8
- C1.7, C2.2, C2.7, C3.1–C3.4 (dịch vụ biên tập; có thể nhận và xử lý thủ công trước khi có đủ màn hình)
- D1.5, D1.6, D2.5, D2.6, D3.1–D3.4, D4.2–D4.4, D5.4

### Giai đoạn sau (P2)
- A1.6, A2.14, A2.15, A3.4, B5.6, B5.7, C1.8, D3.5
- Toàn bộ KV5 (phần mềm nghĩa trang)
- App native
- Đa ngôn ngữ

---

## C. YÊU CẦU PHI CHỨC NĂNG

| Nhóm | Yêu cầu |
|---|---|
| **Hiệu năng** | Trang tưởng niệm mở < 2.5s trên 4G. Ảnh lazy-load, nén nhiều kích cỡ. |
| **Khả dụng** | QR phải mở được trên mọi trình duyệt điện thoại phổ thông, **không cần cài app, không cần đăng nhập**. |
| **Độ bền link** | URL từ QR không đổi khi hồ sơ được sửa, chuyển người quản lý hoặc nâng gói. Mã hồ sơ đã xóa không gán cho người khác. |
| **Khả năng tiếp cận** | Cỡ chữ lớn, tương phản cao — người dùng nhiều tuổi. Hỗ trợ phóng to hệ thống. |
| **Tôn trọng bối cảnh** | Không quảng cáo trên trang tưởng niệm. Không bán dữ liệu gia đình. Không thu phí mở khóa ký ức đã mua và không buộc gia hạn để xem lại. |
| **Sao lưu** | Sao lưu hằng ngày, giữ bản gốc tư liệu, kiểm tra khôi phục hàng tháng. |
| **Riêng tư** | Mặc định Riêng tư, kể cả dữ liệu người còn sống. Người quản lý chủ động chọn phần công khai. Quét QR không cấp quyền. |
| **Bảo mật đường dẫn** | Kiểm tra quyền trên máy chủ đối với trang hồ sơ và từng đường dẫn ảnh, video, tài liệu. Ẩn trên giao diện là chưa đủ. |
| **Xuất dữ liệu** | Gia đình luôn xuất được toàn bộ dữ liệu của mình ở định dạng mở. |

---

**Tài liệu liên quan:**
- [00 — Tổng quan & Đối tượng sử dụng](./00-TONG-QUAN-VA-DOI-TUONG-SU-DUNG.md)
- [02 — Flow chức năng chi tiết](./02-FLOW-CHUC-NANG-CHI-TIET.md)
