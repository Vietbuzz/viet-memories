# KÝ ỨC VIỆT — TÀI LIỆU THIẾT KẾ CHỨC NĂNG
## Phần 2: Flow chức năng chi tiết

> Phiên bản 0.2 — Đã nhập ý kiến cộng tác viên (05/10/2026)
> Mỗi flow gồm: **Ai làm · Điều kiện vào · Các bước · Trạng thái dữ liệu · Ngoại lệ · Điểm đo**
> Trạng thái nội dung, thanh toán, quyền hiển thị và đơn sản xuất được theo dõi riêng.

---

## MỤC LỤC

**Nhóm 1 — Flow người dùng cuối**
- [F1. Quét QR → xem trang tưởng niệm (khách ẩn danh)](#f1)
- [F2. Khách gửi một kỷ niệm](#f2)
- [F3. Đăng ký & tạo không gian gia đình](#f3)
- [F4. Tạo hồ sơ tưởng niệm — tạo nhanh và chỉnh sửa nâng cao](#f4)
- [F5. Mời người thân & cấp quyền](#f5)
- [F6. Người thân đóng góp tư liệu](#f6)
- [F7. Duyệt nội dung & xuất bản](#f7)
- [F8. Mở rộng từ hồ sơ → cây gia phả](#f8)
- [F9. Chuyển giao người quản lý](#f9)
- [F10. Xuất dữ liệu / tạm ẩn / rời dịch vụ](#f10)

**Nhóm 2 — Flow kinh doanh & vận hành**
- [F11. Hành trình khách hàng 6 bước (end-to-end)](#f11)
- [F12. Từ lead đến đơn hàng](#f12)
- [F13. Quy trình biên tập khi khách thuê dịch vụ](#f13)
- [F14. Sản xuất & bàn giao QR vật lý](#f14)
- [F15. Đối tác bia mộ và hoa hồng theo thỏa thuận](#f15)

**Nhóm 3 — Flow hệ thống**
- [F16. Xử lý dữ liệu mâu thuẫn / trùng lặp](#f16)
- [F17. Quy tắc AI trong quy trình](#f17)

---
---

# NHÓM 1 — FLOW NGƯỜI DÙNG CUỐI

<a id="f1"></a>
## F1. Quét QR → xem trang tưởng niệm

**Ai:** Khách ẩn danh (người viếng mộ, người được chia sẻ link)
**Điều kiện vào:** Hồ sơ đã kích hoạt và có ít nhất một phần mức Công khai
**Nền tảng:** Mobile (99% trường hợp)

### Các bước
```
1. Quét QR số, bảng mica, bảng kim loại hoặc bảng gốm
        ↓
2. Trình duyệt mở kyucviet.vn/h/{ma-ho-so}
        ↓
3. Hiển thị ngay khối đầu trang mà gia đình đã cho công khai:
   ảnh chân dung · tên · năm sinh–năm mất · câu trích dẫn
        ↓
4. Người xem cuộn/chuyển tab:
   Câu chuyện → Dấu mốc → Album → Người thân → Nơi an nghỉ
        ↓
5. Lối rẽ CTA:
   ┌─ [Chia sẻ] ──────→ Zalo / FB / sao chép link     (P0)
   ├─ [Gửi một kỷ niệm] → F2                           (P0)
   └─ [Tôi là người thân] → F5 hướng B                 (P1)
```

### Quy tắc hiển thị
| Tình huống | Kết quả |
|---|---|
| Khách ẩn danh | Chỉ thấy nội dung mức **Công khai** |
| Đã đăng nhập, là thành viên gia đình | Thấy thêm nội dung mức **Gia đình** (có nhãn 👨‍👩‍👧) |
| Đã đăng nhập, là người quản lý | Thấy thêm nút **Chỉnh sửa** ở mỗi khối |

### Ngoại lệ
| Tình huống | Xử lý |
|---|---|
| Hồ sơ chưa kích hoạt hoặc chưa có phần công khai | Trang "Hồ sơ đang được gia đình hoàn thiện" + nút Liên hệ. Không lộ nội dung Riêng tư |
| Hồ sơ đã kích hoạt nhưng gia đình giữ riêng tư | Trang ngắn: gia đình chưa mở nội dung công khai. Không xem là hết hạn |
| Hồ sơ tạm ẩn | Trang "Hồ sơ tạm ngừng hiển thị" + hướng dẫn liên hệ người quản lý. Dữ liệu và quyền lưu trữ đã mua vẫn còn |
| QR hỏng, không có mã hợp lệ | Trang tra cứu thủ công (nhập tên + năm mất) |
| Mạng yếu tại nghĩa trang | Ưu tiên tải khối đầu trang trước; ảnh album tải sau; có bản nhẹ |

### Trạng thái dữ liệu
`Đã xuất bản` → không đổi (chỉ ghi log lượt quét)

### Điểm đo
- Lượt quét / hồ sơ · Thời gian ở lại · Tỷ lệ bấm "Gửi kỷ niệm" · Tỷ lệ chia sẻ

---

<a id="f2"></a>
## F2. Khách gửi một kỷ niệm

**Ai:** Khách ẩn danh hoặc người thân chưa có tài khoản
**Điều kiện vào:** Đang xem trang tưởng niệm công khai

### Các bước
```
1. Bấm [Gửi một kỷ niệm]
        ↓
2. Form (ngắn, không bắt đăng ký):
   • Bạn là ai với người này?  (bắt buộc)
   • Tên bạn                    (bắt buộc)
   • SĐT hoặc email             (bắt buộc — để gia đình xác minh)
   • Lời kể / kỷ niệm           (tùy chọn)
   • Ảnh kèm (tối đa 5)         (tùy chọn)
        ↓
3. Gửi → Hiện thông báo:
   "Cảm ơn bạn. Nội dung sẽ được gia đình xem và duyệt trước khi hiển thị."
        ↓
4. Hệ thống tạo bản ghi ĐÓNG GÓP, trạng thái = Chờ duyệt
        ↓
5. Thông báo tới người quản lý hồ sơ (Zalo/SMS/email + badge trong app)
        ↓
6. → F7 (Duyệt nội dung)
```

### Ngoại lệ & chống lạm dụng
| Tình huống | Xử lý |
|---|---|
| Spam / nội dung xấu | Giới hạn tần suất theo IP; lọc từ khóa; gia đình có nút "Chặn người gửi" |
| Ảnh quá lớn / sai định dạng | Nén phía client, báo lỗi rõ ràng |
| Gia đình không phản hồi > 30 ngày | Nhắc lại 1 lần; sau 90 ngày tự lưu trữ (không xóa) |

### Trạng thái dữ liệu
`Chờ duyệt` → (F7) → `Đã duyệt` / `Từ chối` / `Lưu trữ`

### Điểm đo
**Chỉ số then chốt:** % hồ sơ có đóng góp từ người thứ hai — mục tiêu **≥ 30%**

---

<a id="f3"></a>
## F3. Đăng ký & tạo không gian gia đình

**Ai:** Con cháu đứng ra tổ chức (người mua)

### Các bước
```
1. Vào từ: trang giới thiệu / link tư vấn / nút "Tôi là người thân"
        ↓
2. Nhập số điện thoại → nhận OTP → xác thực
        ↓
3. Khai tên hiển thị + ảnh (tùy chọn)
        ↓
4. Tạo không gian gia đình:
   • Tên không gian (vd: "Gia đình Nguyễn")
   • Bạn là ai trong gia đình
        ↓
5. Hệ thống gán vai trò NGƯỜI QUẢN LÝ GIA ĐÌNH
        ↓
6. Màn hình chào:
   ┌─ [Tạo hồ sơ người thân đầu tiên] → F4
   ├─ [Tải ảnh lên kho trước]          → B3
   └─ [Xem hồ sơ mẫu]                  → A1.2
```

### Ngoại lệ
| Tình huống | Xử lý |
|---|---|
| SĐT đã tồn tại | Chuyển sang đăng nhập; hỏi "Bạn muốn vào không gian nào?" |
| Đội vận hành tạo hộ (dịch vụ) | A6 tạo không gian + hồ sơ, sau đó **chuyển quyền quản lý cho gia đình** ở bước bàn giao (F13.6) |

---

<a id="f4"></a>
## F4. Tạo hồ sơ tưởng niệm — TẠO NHANH VÀ CHỈNH SỬA NÂNG CAO ⭐

**Ai:** Người quản lý gia đình. A4 chỉ vào khi khách thuê dịch vụ biên tập (F13, P1)
**Nền tảng:** Tạo nhanh dùng được trên điện thoại và máy tính. Chỉnh sửa nâng cao ưu tiên máy tính, có bản mobile rút gọn

### Lối A — Tạo nhanh (P0)

```
1. Nhập thông tin cơ bản: ảnh, họ tên, năm sinh, năm mất, câu chuyện ngắn
        ↓
2. Tải thêm ảnh nếu có
        ↓
3. Hệ thống tự trình bày theo mẫu:
   bố trí ảnh, tiểu sử, dấu mốc, album
   ẩn các mục đang trống
   xem đẹp trên máy tính và điện thoại
        ↓
4. Xem trước ngay — không cần đi hết bảy nhóm nội dung
        ↓
5. Bản nháp được lưu. Khách chọn gói và thanh toán ở F11
```

Sau thanh toán, bản nháp thành hồ sơ lưu theo gói. Nội dung đã nhập được giữ nguyên.

### Vòng đời bản nháp chưa thanh toán

- Ghi số ngày được lưu, thời điểm bắt đầu tính, nhắc trước hạn và việc xảy ra khi hết hạn.
- **Số ngày chưa chốt** (xem mục 11 của tài liệu 00).
- Hết hạn chỉ áp dụng cho bản nháp chưa thanh toán. Hồ sơ đã mua không đi vào vòng đời này.
- Nhắc bỏ dở sau 3 ngày và 7 ngày vẫn là nhắc quay lại, khác với hạn xóa hoặc khóa bản nháp.

### Lối B — Chỉnh sửa nâng cao (P0, không chặn xem trước)

**Bố cục màn hình:** Danh sách nhóm (trái) · Form (giữa) · **Xem trước trực tiếp (phải)**

```
┌───────────┬─────────────────────────┬──────────────────┐
│ 1 Cơ bản  │  Chỉnh sửa hồ sơ        │  BẢN XEM TRƯỚC   │
│ 2 Chuyện  │  [Bản nháp] ✓ Đã lưu    │  (Chưa xuất bản) │
│ 3 Ảnh     │                          │  ┌────────────┐  │
│ 4 Người   │  [form fields...]        │  │ ảnh bìa    │  │
│ 5 Nơi AN  │                          │  │ Nguyễn V.B │  │
│ 6 Quyền   │                          │  │ 1940–2020  │  │
│ 7 Hoàn tất│  [Lưu nháp] [Tiếp →]     │  └────────────┘  │
└───────────┴─────────────────────────┴──────────────────┘
        [Xem trước]  [Gửi gia đình duyệt]
```

### Bước 1 — Thông tin cơ bản
| Trường | Bắt buộc | Ghi chú |
|---|:--:|---|
| Ảnh chân dung | ○ | Gợi ý: "Chọn ảnh rõ mặt, ánh sáng tự nhiên" |
| Họ và tên | ● | |
| Năm sinh | ○ | *"Có thể chỉ nhập năm khi chưa rõ ngày, tháng"* |
| Năm mất | ○ | |
| Quê quán | ○ | |
| Nghề nghiệp | ○ | |
| Lời giới thiệu ngắn | ○ | vd: "Người cha, người thầy và người ông kính yêu" |
| Nguồn thông tin | ● | vd: "Gia đình cung cấp" |
| ☐ Cần xác nhận thêm với người thân | ○ | Gắn cờ chờ xác nhận |

> 🔑 **Nguyên tắc thiết kế:** *"Thông tin chưa rõ có thể để trống hoặc đánh dấu chờ xác nhận."* Không được ép nhập đủ — đây là rào cản bỏ dở lớn nhất.

### Bước 2 — Câu chuyện cuộc đời
- Ô soạn thảo tiểu sử (rich text đơn giản: đậm, nghiêng, đoạn, trích dẫn)
- **Các dấu mốc:** thêm từng mốc `Năm · Tiêu đề · Mô tả · Ảnh kèm`
- Gợi ý câu hỏi dẫn dắt: *Ông/bà sinh ra ở đâu? Làm nghề gì? Kỷ niệm nào con cháu nhớ nhất?*
- (P1) Nút **"AI gợi ý viết"** → sinh bản nháp từ tư liệu đã có, **gắn nhãn "Bản AI soạn — cần duyệt"**

### Bước 3 — Ảnh & tư liệu
- Chọn từ Kho tư liệu (B3) hoặc tải mới ngay tại đây
- Sắp xếp thành album, đặt tên album (vd: "Bên hiên nhà", "Ngày sum họp")
- Viết chú thích từng ảnh
- Chọn **ảnh bìa** và **ảnh chân dung**

### Bước 4 — Người thân
- Thêm quan hệ: Cha · Mẹ · Vợ/Chồng · Con · Anh chị em
- Mỗi người: **liên kết hồ sơ đã có** hoặc **tạo thành viên tối giản** (chỉ tên + năm)
- Thành viên tối giản không phát sinh phí. Hồ sơ tưởng niệm trả phí là một lần mua riêng
- Dữ liệu người còn sống không mặc định công khai
- Hệ thống cảnh báo nếu phát hiện hồ sơ trùng → F16
- Đây là cầu nối sang gia phả (F8, P1)

### Bước 5 — Nơi an nghỉ
- Nghĩa trang / địa điểm · Khu – Lô – Hàng – Mộ · Tọa độ (chọn trên bản đồ) · Ảnh khu mộ
- **Ngày giỗ âm lịch** (vd: 18 tháng Ba âm lịch) — hệ thống tự quy đổi sang dương lịch hằng năm
- Ghi chú đường đi

### Bước 6 — Quyền hiển thị

Mọi khối **mặc định Riêng tư**. Người quản lý chủ động chọn phần Công khai hoặc Gia đình. Hồ sơ đã trả phí vẫn kích hoạt được khi chưa mở gì ra công khai.

| Khối nội dung | Công khai | Gia đình | Riêng tư |
|---|:--:|:--:|:--:|
| Tên, ảnh, năm sinh–mất | ○ | ○ | ◉ |
| Lời giới thiệu ngắn | ○ | ○ | ◉ |
| Câu chuyện cuộc đời | ○ | ○ | ◉ |
| Album ảnh | ○ | ○ | ◉ |
| Người thân | ○ | ○ | ◉ |
| Nơi an nghỉ | ○ | ○ | ◉ |
| Giấy tờ, liên hệ | ○ | ○ | ◉ |

Cảnh báo cố định: **"Quét QR không tự cấp quyền xem tư liệu riêng."** Đường dẫn ảnh, video và tài liệu cũng phải được kiểm tra quyền trên máy chủ.

### Bước 7 — Kiểm tra & hoàn tất
Checklist bắt buộc tick đủ:
- ☐ Xác nhận tên và ngày tháng
- ☐ Kiểm tra quyền hiển thị
- ☐ Gia đình duyệt nội dung

→ Nút **[Gửi gia đình duyệt]**

### Trạng thái nội dung

Thanh toán, quyền hiển thị và đơn sản xuất không nằm trên sơ đồ này.

```
Nháp ──[Gửi duyệt]──▶ Chờ duyệt nội dung ──[Chủ hồ sơ duyệt]──▶ Nội dung đã duyệt
  ▲                         │
  └────[Yêu cầu sửa]────────┘

Nội dung đã duyệt + Đã thanh toán + Đã chọn quyền hiển thị ──▶ Đã kích hoạt (F7)
```

Bản nháp chưa thanh toán có thể hết hạn theo quy tắc chưa chốt ở trên. Hồ sơ đã kích hoạt không có trạng thái quá hạn.

### Ngoại lệ
| Tình huống | Xử lý |
|---|---|
| Mất mạng giữa chừng | Tự lưu nháp cục bộ, đồng bộ khi có mạng lại |
| Bỏ dở nhiều ngày | Nhắc qua Zalo/email sau 3 ngày và 7 ngày, kèm link quay lại đúng bước đang dở |
| Nhiều người cùng sửa | Khóa mềm theo bước + cảnh báo "A đang sửa bước này" |
| Không có ảnh chân dung | Dùng ảnh mặc định trang nhã, vẫn xuất bản được |

### Điểm đo ⭐
**Tỷ lệ hoàn tất hồ sơ — mục tiêu ≥ 60%.** Đo riêng lối tạo nhanh và điểm bỏ dở từng nhóm của chỉnh sửa nâng cao.

---

<a id="f5"></a>
## F5. Mời người thân & cấp quyền

**Ai:** Người quản lý gia đình

```
Hướng A — Chủ động mời:
1. Vào hồ sơ → tab Người thân → [Mời người thân]
2. Nhập SĐT / chọn từ danh bạ / tạo link mời
3. Chọn vai trò: Thành viên (chỉ xem) | Người đóng góp (gửi tư liệu, sửa nháp)
4. Gửi qua Zalo / SMS / sao chép link
5. Người được mời mở link → đăng nhập bằng OTP → vào không gian gia đình
6. Hệ thống ghi log: ai mời, mời ai, vai trò gì, lúc nào

Hướng B — Yêu cầu từ ngoài vào (P1, không nằm trong MVP):
1. Khách bấm [Tôi là người thân] trên trang công khai
2. Khai: quan hệ với người này + tên + SĐT
3. → Hàng chờ "Yêu cầu kết nối" của người quản lý
4. Người quản lý duyệt/từ chối, chọn vai trò khi duyệt
```

### Ngoại lệ
| Tình huống | Xử lý |
|---|---|
| Link mời bị chuyển tiếp cho người lạ | Link mời **có hạn 7 ngày**, dùng 1 lần, gắn với SĐT nếu đã nhập |
| Người được mời không dùng smartphone | Cho phép người quản lý nhập hộ tư liệu, ghi rõ "Do [tên] cung cấp" |
| Thu hồi quyền | Người quản lý gỡ thành viên bất kỳ lúc nào; nội dung họ đã đóng góp **được giữ lại** kèm ghi nguồn |

### Điểm đo
**Số người thân được mời / hồ sơ — mục tiêu ≥ 2.**

---

<a id="f6"></a>
## F6. Người thân đóng góp tư liệu

**Ai:** Người đóng góp (đã được mời), thường là người lớn tuổi hoặc họ hàng

```
1. Mở link / mở app → vào hồ sơ
2. [Gửi ký ức] hoặc [Thêm ảnh]
3. Chọn hình thức:
   ├─ Tải ảnh từ máy
   ├─ Chụp ảnh cũ bằng camera        (mobile)
   ├─ Ghi âm lời kể trực tiếp         (P1)
   └─ Viết lời kể
4. Gắn thẻ: ai trong ảnh · năm nào · ở đâu
5. Xác nhận quyền sử dụng: ☐ Tôi đồng ý cho gia đình sử dụng tư liệu này
6. Gửi → trạng thái Chờ duyệt
7. Người quản lý nhận thông báo → F7
```

> 🔒 **Quy tắc:** Người đóng góp **không được ghi đè dữ kiện đã duyệt**. Muốn sửa thông tin đã có → tạo **"Đề nghị sửa"**, người quản lý quyết định.

---

<a id="f7"></a>
## F7. Duyệt nội dung & xuất bản

**Ai:** Người quản lý gia đình (duyệt nội dung) · A5 (kỹ thuật phát hành)

```
1. Vào Hàng chờ duyệt — gồm:
   • Đóng góp từ khách ẩn danh (F2)
   • Đóng góp từ người thân (F6)
   • Đề nghị sửa dữ kiện
   • Hồ sơ vừa hoàn tất wizard (F4)
        ↓
2. Mở từng mục:
   • Xem nội dung + người gửi + thời gian
   • (Với đề nghị sửa) Xem so sánh TRƯỚC / SAU
        ↓
3. Quyết định:
   ├─ [Duyệt]         → Nội dung vào hồ sơ, ghi log
   ├─ [Yêu cầu sửa]   → Trả về người gửi kèm lý do
   └─ [Từ chối]       → Lưu trữ, không hiển thị, vẫn giữ log
        ↓
4. [Kích hoạt hồ sơ] chỉ mở khi đủ cả ba:
   • Đã xác nhận thanh toán
   • Chủ hồ sơ đã duyệt nội dung
   • Đã xác nhận quyền hiển thị
        ↓
5. Hệ thống:
   • Sinh URL ổn định: kyucviet.vn/h/{ma}
   • Gắn mã QR số với URL đó — mã này không đổi và không được cấp lại cho người khác nếu hồ sơ bị xóa
   • Ghi phiên bản, timestamp và người duyệt
   • Thông báo cho thành viên gia đình
   • Nếu chưa có khối nào mức Công khai, hồ sơ vẫn kích hoạt nhưng trang quét QR không lộ nội dung
```

### Quy tắc bất biến
1. **Mọi nội dung AI sinh ra phải qua bước duyệt của người thật** trước khi hiển thị công khai.
2. **URL không đổi** sau lần kích hoạt đầu, kể cả khi sửa nội dung, nâng gói hoặc chuyển quản lý.
3. **Lịch sử thay đổi không được xóa** — chỉ thêm.
4. Tạm ẩn chỉ giấu khỏi công khai. Không xóa dữ liệu và không mất quyền lưu trữ đã mua.
5. Hồ sơ trả phí có thể giữ riêng tư. Kích hoạt không buộc công khai.

### Điểm đo
Thời gian trung bình từ "gửi duyệt" → "xuất bản". Số vòng sửa / hồ sơ.

---

<a id="f8"></a>
## F8. Mở rộng từ hồ sơ → cây gia phả *(P1)*

**Điều kiện kích hoạt:** Gia đình đã khai ≥ 3 quan hệ ở Bước 4 của wizard

```
1. Hệ thống gợi ý trên bảng điều khiển:
   "Gia đình bạn đã có 5 người thân — xem cây gia đình?"
        ↓
2. Mở Cây gia phả: hiển thị theo thế hệ, thu/phóng được
        ↓
3. Từ mỗi nút:
   ├─ [Thêm cha/mẹ]  → mở rộng lên trên (tổ tiên)
   ├─ [Thêm con]      → mở rộng xuống dưới
   ├─ [Thêm vợ/chồng] → mở rộng ngang
   └─ [Xem hồ sơ]     → sang trang tưởng niệm
        ↓
4. Mỗi người mới thêm = một thành viên tối giản (tên + năm)
   → không tự phát sinh phí
   → muốn thành hồ sơ tưởng niệm thì mua gói riêng, giữ quan hệ đã khai
        ↓
5. Quan hệ mới có trạng thái "Đề xuất" cho tới khi
   người quản lý hoặc người thân liên quan XÁC NHẬN
        ↓
6. Khi cây vượt 1 gia đình → gợi ý tạo KHÔNG GIAN DÒNG HỌ
   với quản trị viên riêng và phân quyền theo nhánh
```

### Ngoại lệ
| Tình huống | Xử lý |
|---|---|
| Hai nhánh cùng khai một tổ tiên | → F16 (xử lý trùng lặp) |
| Quan hệ mâu thuẫn (A vừa là con vừa là anh của B) | Gắn nhãn "Mâu thuẫn", giữ cả hai, chờ đại diện quyết |
| Vòng lặp trong cây | Chặn ở tầng validate, báo lỗi rõ |

---

<a id="f9"></a>
## F9. Chuyển giao người quản lý

**Vì sao cần:** người quản lý có thể qua đời hoặc không còn khả năng quản lý — đây là rủi ro tồn tại của sản phẩm di sản.

```
Hướng A — Chủ động chuyển:
1. Người quản lý → Cài đặt → [Chuyển quyền quản lý]
2. Chọn thành viên trong gia đình
3. Người nhận xác nhận qua OTP
4. Hai bên nhận thông báo; ghi log; quyền chuyển ngay

Hướng B — Người quản lý không còn khả năng:
1. Thành viên gia đình gửi [Yêu cầu tiếp quản] kèm lý do
2. Hệ thống thông báo người quản lý hiện tại + toàn bộ thành viên
3. Chờ 14 ngày — nếu người quản lý phản đối → dừng
4. Nếu không phản đối → A6/A8 xác minh (giấy tờ, xác nhận từ ≥ 2 thành viên)
5. Chuyển quyền, ghi log đầy đủ
```

**Bắt buộc từ MVP:** mỗi hồ sơ phải khai **người quản lý dự phòng**. Hướng B được xử lý thủ công, có xác minh, ngay trong MVP.

---

<a id="f10"></a>
## F10. Xuất dữ liệu / Tạm ẩn / Rời dịch vụ

Hồ sơ đã mua không có luồng gia hạn và không bị ẩn vì quá hạn. Khách không phải gia hạn để xem lại ký ức.

```
TẠM ẨN  (P0)
1. Người quản lý chọn [Tạm ẩn]
2. Trang công khai và QR không còn hiện nội dung
3. Dữ liệu, đường dẫn và quyền lưu trữ đã mua được giữ
4. Bỏ ẩn thì trang hiện lại theo quyền hiển thị đang chọn

XUẤT DỮ LIỆU  (quyền của gia đình, luôn có)
1. Cài đặt → [Xuất dữ liệu]
2. Chọn phạm vi: một hồ sơ / cả không gian gia đình
3. Hệ thống đóng gói: ảnh và tư liệu bản gốc + JSON dữ liệu + PDF trang tưởng niệm
4. Gửi link tải (có hạn 7 ngày) qua email

RỜI DỊCH VỤ
1. Yêu cầu ngừng → bắt buộc xuất dữ liệu trước
2. Xác nhận 2 lần, cách nhau 7 ngày
3. Gỡ hiển thị công khai
4. Giữ dữ liệu thêm 90 ngày (cho phép khôi phục) rồi mới xóa
5. Mã hồ sơ và QR của hồ sơ đã xóa không gán cho người khác

YÊU CẦU XÓA  (P0, xử lý thủ công trong MVP)
1. Người quản lý gửi yêu cầu xóa, ghi rõ phạm vi
2. A8 xác minh danh tính
3. Xóa theo phạm vi đã xác nhận, ghi log
4. Xóa tự động toàn trình làm ở giai đoạn sau
```

> Giao diện nói: *"thanh toán một lần, lưu trữ trọn đời theo phạm vi gói đã công bố"*. Không dùng "vĩnh viễn không điều kiện". Vòng đời có hạn chỉ áp dụng cho **bản nháp chưa thanh toán** (F4).

---
---

# NHÓM 2 — FLOW KINH DOANH & VẬN HÀNH

<a id="f11"></a>
## F11. Hành trình khách tự mua (end-to-end) ⭐

Đây là hành trình P0. Bảng QR vật lý không còn bắt buộc đi kèm mọi hồ sơ.

```
Tạo bản nháp → Xem trước → Chọn Basic hoặc gói cao hơn
      → Tùy chọn bảng QR và dịch vụ → Thanh toán
      → Kích hoạt hồ sơ → Sản xuất và giao bảng nếu có
```

| Bước | Việc | Ghi chú |
|---|---|---|
| 1 | Tạo bản nháp | F4 lối tạo nhanh |
| 2 | Xem trước | Theo mẫu, ẩn mục trống |
| 3 | Chọn gói | Basic dưới 100.000đ/hồ sơ, hoặc gói dung lượng cao hơn |
| 4 | Tùy chọn | Bảng mica, kim loại, gốm; hoặc dịch vụ video. Bỏ qua được |
| 5 | Thanh toán | Một lần. Trạng thái chờ / lỗi / thành công. Không tạo đơn trùng |
| 6 | Kích hoạt | F7: đã trả tiền, nội dung được duyệt, quyền hiển thị đã chọn |
| 7 | Giao bảng | Chỉ khi có mua bảng. F14 |

Sau kích hoạt, khách mời người thân và bổ sung ký ức trên cùng hồ sơ. Nâng dung lượng, mua thêm bảng hoặc đặt video không tạo hồ sơ mới.

Khách muốn đội ngũ viết hộ đi theo F12 và F13. Đó là dịch vụ P1, không phải cổng bắt buộc của hành trình này.

### Ba nguyên tắc trải nghiệm (kiểm tra mọi màn hình theo 3 tiêu chí này)
| Nguyên tắc | Nghĩa là |
|---|---|
| 🚀 **Dễ bắt đầu** | Luôn có hướng dẫn gửi tư liệu; không màn hình trống |
| 🛡 **Dễ kiểm soát** | Luôn xem trước được, sửa được, chọn được ai xem |
| 🔧 **Dễ duy trì** | Có hỗ trợ, sao lưu và xuất dữ liệu |

### Điểm đo
Theo dõi **điểm bỏ dở**, **thời gian hoàn tất từng bước**, và **lý do khách cần hỗ trợ**.

---

<a id="f12"></a>
## F12. Từ lead đến đơn hàng

Đơn tự phục vụ (F11) do khách tạo và thanh toán, không đi qua lead. Luồng dưới đây dành cho khách cần tư vấn hoặc thuê biên tập.

```
A2 tìm lead   →  A3 chuẩn bị  →  Partner xác  →  Báo giá      →  Khách    →  A7 ghi nhận
(có nguồn)       tư vấn          nhận nhu cầu     được duyệt      đồng ý      theo chứng từ
```

| Bước | Ai | Việc | Đầu ra hệ thống |
|---|---|---|---|
| 1 | A2 | Tìm lead có nguồn rõ ràng | Bản ghi lead + trường "nguồn" |
| 2 | A3 | Chuẩn bị nội dung tư vấn | Mẫu tư vấn, hồ sơ mẫu để gửi |
| 3 | Partner | Xác nhận nhu cầu thật | Ghi chú nhu cầu vào CRM |
| 4 | A3 | Lập báo giá | Báo giá nháp → **founder duyệt** → gửi |
| 5 | Khách | Đồng ý | Chuyển lead → đơn hàng |
| 6 | A7 | Ghi nhận thanh toán theo chứng từ | Bản ghi thu |

### 🚫 Rào chắn bắt buộc (đưa vào hệ thống, không chỉ là quy ước)
> **Không tự gửi email, chỉ quảng cáo hoặc cam kết giá khi chưa có ủy quyền.**
Hệ thống phải chặn: gửi báo giá, gửi email hàng loạt, ký kết — nếu chưa có người thật bấm duyệt.

---

<a id="f13"></a>
## F13. Quy trình biên tập khi khách thuê dịch vụ ⭐

Chỉ áp dụng khi khách đặt dịch vụ biên tập (C3, P1). Giai đoạn đầu có thể vận hành thủ công. Đơn tự phục vụ không đi qua A4.

Đơn có bảng QR đi theo F14, tách khỏi trạng thái nội dung của hồ sơ.

```
1. A6 TIẾP NHẬN
   ├ Thu tư liệu từ khách
   ├ Xác định người quản lý hồ sơ
   ├ Lấy đồng thuận gia đình
   └ Chốt quyền hiển thị
        ↓
2. A4 BIÊN TẬP
   ├ Soạn tiểu sử, album, dòng thời gian
   └ ĐÁNH DẤU những điều chưa rõ (không bịa)
        ↓
3. A8 KIỂM TRA
   ├ Soát dữ kiện & nguồn
   ├ Soát quyền hiển thị
   └ Soát điều kiện kích hoạt (thanh toán, nội dung, quyền hiển thị)
        ↓
4. GIA ĐÌNH XÁC NHẬN
   ├ Sửa tên, ngày, quan hệ
   └ DUYỆT BẢN CUỐI              ← cổng bắt buộc
        ↓
5. FOUNDER DUYỆT · A5 KÍCH HOẠT
   ├ Đủ thanh toán, nội dung đã duyệt, quyền hiển thị đã chọn
   └ Sinh và liên kết QR ổn định nếu chưa có
        ↓
6. A6 BÀN GIAO
   ├ Quét thử QR số bằng điện thoại
   ├ Hướng dẫn gia đình sử dụng
   ├ CHUYỂN QUYỀN QUẢN LÝ cho gia đình
   └ Ghi nhận bàn giao nội dung
        ↓
7. A7 ĐỐI SOÁT · A1 TỔNG HỢP
   ├ Thu chi
   ├ Hoa hồng chỉ nếu có thỏa thuận riêng
   └ Ghi lỗi và bài học
```

### Điều kiện hoàn tất một đơn biên tập
- ☐ Nội dung được gia đình duyệt
- ☐ Đã thanh toán phần dịch vụ đã chốt
- ☐ QR số mở đúng hồ sơ
- ☐ Quyền truy cập đúng như đã thống nhất
- ☐ Khách nhận hướng dẫn sử dụng
- ☐ Lưu biên bản bàn giao nội dung

### Yêu cầu hệ thống
- Mỗi đơn có **một mã đơn xuyên suốt** cả 7 bước
- Mỗi bước có **một người chủ trì** và **một người duyệt**
- Theo dõi **đúng hẹn** và **công hỗ trợ sau giao**

---

<a id="f14"></a>
## F14. Sản xuất & giao bảng QR vật lý

Chỉ chạy khi khách mua bảng. Hồ sơ Basic không đi vào luồng này. Công ty không khắc đá, không lắp tại mộ và không nghiệm thu tại hiện trường.

```
1. Hồ sơ đã có URL ổn định và mã QR số
        ↓
2. Khách chọn bảng: Mica (trong nhà) | Kim loại cao cấp | Gốm (khi đã mở bán)
   Kim loại: màu vàng, bạc, đồng, trắng sáng
   Gốm: chờ chốt mẫu; phụ kiện lắp theo thiết kế riêng, không dùng cách khoan của kim loại
        ↓
3. Khách duyệt mẫu: tên, ngày tháng, bố cục
   Trạng thái: Chờ duyệt mẫu
        ↓
4. Sản xuất → Kiểm tra QR (quét thử, mở đúng trang) → Đóng gói → Vận chuyển → Đã giao
   Gốm thêm: kiểm tra quét, đóng gói chống vỡ, cách xử lý nếu vỡ khi giao
        ↓
5. Giao bảng đã khoan sẵn (nếu loại bảng cần khoan) và phụ kiện phù hợp
   Khách tự lắp
```

Khắc lên đá do đối tác bia mộ làm và thu tiền. Công ty chỉ cấp QR số và thu phí nền tảng (F15).

### Ngoại lệ
| Tình huống | Xử lý |
|---|---|
| QR mờ, khó quét, giao sai hoặc hỏng | Làm lại theo chính sách; ghi nhật ký sự cố (A8). Khách báo qua B6.8 |
| Bảng hỏng hoặc mất sau này | Cấp lại bảng, giữ nguyên URL — không sinh mã mới |
| Nâng gói hoặc sửa hồ sơ | URL không đổi |
| Gốm vỡ khi vận chuyển | Xử lý theo cam kết đóng gói chống vỡ, không dùng quy cách kim loại |

---

<a id="f15"></a>
## F15. Đối tác bia mộ và hoa hồng theo thỏa thuận *(P1)*

```
ĐỐI TÁC BIA MỘ
1. Gia đình muốn khắc QR lên đá
        ↓
2. Công ty thu phí nền tảng và cấp mã QR số
        ↓
3. Đối tác tự báo giá, tự thu tiền khắc đá, tự sản xuất phần đá
        ↓
4. Không mặc định khoản hoa hồng thêm từ công ty

ĐỐI TÁC GIỚI THIỆU KHÁC
1. A3 ký thỏa thuận riêng: nguồn đơn, trách nhiệm, hoa hồng, cách đối soát
        ↓
2. Cấp mã giới thiệu + bộ công cụ
   ├ Một hồ sơ mẫu + QR thử
   ├ Bảng gói (Basic, nâng dung lượng, bảng QR, dịch vụ video)
   └ Mẫu lời giới thiệu
        ↓
3. Đơn gắn mã nguồn
        ↓
4. Chỉ khi có thỏa thuận: A7 đối soát và trả hoa hồng
        ↓
5. Đánh giá đối tác có đơn lặp lại (KPI: ≥ 3 đối tác tiếp tục)
```

> Đối tác không truy cập dữ liệu gia đình. Cổng đối tác (D3.5, P2) nếu làm sau chỉ hiện đơn do mình giới thiệu và trạng thái. Hoa hồng chỉ hiện khi thỏa thuận có khoản đó.

---
---

# NHÓM 3 — FLOW HỆ THỐNG

<a id="f16"></a>
## F16. Xử lý dữ liệu mâu thuẫn / trùng lặp

```
PHÁT HIỆN (tự động)
├ Trùng họ tên + năm sinh/mất gần nhau
├ Hai nguồn khai khác nhau về cùng một dữ kiện
└ Quan hệ mâu thuẫn logic
        ↓
GẮN NHÃN "CHỜ XÁC NHẬN"  — hiển thị cảnh báo cho người quản lý
        ↓
GIỮ NGUYÊN CẢ HAI NGUỒN + toàn bộ lịch sử
   ❌ KHÔNG tự động gộp
   ❌ KHÔNG tự động chọn bên nào đúng
        ↓
ĐẠI DIỆN CÓ THẨM QUYỀN QUYẾT ĐỊNH
├ Gộp hai hồ sơ (chọn dữ kiện giữ lại từng trường)
├ Xác nhận là hai người khác nhau
└ Để nguyên trạng thái chờ
        ↓
GHI LOG: ai quyết, quyết gì, dựa vào đâu
```

**Giao diện cần có:** màn hình so sánh hai bên cạnh nhau, chọn từng trường, xem nguồn của từng dữ kiện.

---

<a id="f17"></a>
## F17. Quy tắc AI trong quy trình

### AI được làm
| Việc | Vai trò | Đầu ra |
|---|---|---|
| Phân loại, sắp xếp ảnh theo thời gian/chủ đề | A4 | Đề xuất album |
| Chép lời kể từ file ghi âm (speech-to-text) | A4 | Bản nháp văn bản |
| Soạn nháp tiểu sử từ tư liệu đã có | A4 | Bản nháp, **gắn nhãn "AI soạn"** |
| Gợi ý dấu mốc thời gian | A4 | Danh sách đề xuất |
| Phục hồi/làm nét ảnh cũ | A4 | Phiên bản mới, **giữ bản gốc** |
| Soát tên/ngày/quan hệ, phát hiện trùng | A8 | Danh sách cảnh báo |
| Nhắc việc, tổng hợp báo cáo | A1, A6 | Bản tin nội bộ |

### AI KHÔNG được làm *(rào chắn kỹ thuật, không chỉ quy ước)*
- ❌ **Tự tạo dữ kiện** — không suy đoán năm sinh, quan hệ, sự kiện không có trong tư liệu
- ❌ **Tự công bố** — mọi đầu ra đều ở trạng thái đề xuất
- ❌ **Tự gửi ra ngoài** — email, tin nhắn tới khách phải người thật bấm gửi
- ❌ **Tự chi tiền, ký kết, đổi quyền, xóa dữ liệu**
- ❌ **Tự quyết định tranh chấp dữ liệu**
- ❌ **Truy cập nội dung mức Riêng tư** (trừ phần cần làm, có nhật ký)

### Yêu cầu minh bạch trên giao diện
Mọi nội dung có AI tham gia phải hiển thị nhãn: **"Do AI hỗ trợ xử lý — gia đình đã xác nhận"** hoặc **"Bản AI soạn — chưa duyệt"**.

---

## PHỤ LỤC A — Sơ đồ trạng thái tổng hợp

Bốn nhóm trạng thái dưới đây không gộp thành một trạng thái hồ sơ.

### Trạng thái nội dung
```
Nháp ──▶ Chờ duyệt nội dung ──▶ Nội dung đã duyệt ──▶ Đã kích hoạt
  ▲              │                                      │
  └──────────────┘                                      ▼
     (yêu cầu sửa)                                   Tạm ẩn
```

Hồ sơ đã thanh toán không có trạng thái quá hạn. Bản nháp chưa thanh toán có hạn lưu riêng; số ngày chưa chốt.

### Trạng thái thanh toán
```
Chưa thanh toán ──▶ Chờ xác nhận ──▶ Thành công
                         │
                         └──▶ Lỗi ──▶ Chờ xác nhận (thanh toán lại)
```

### Trạng thái quyền hiển thị

Mỗi khối nội dung một mức: **Riêng tư** (mặc định) · **Gia đình** · **Công khai**. Đổi mức không đổi trạng thái thanh toán hay đơn sản xuất.

### Trạng thái Đóng góp
```
Chờ duyệt ──▶ Đã duyệt (hiển thị)
     ├──────▶ Yêu cầu sửa ──▶ Chờ duyệt
     ├──────▶ Từ chối (lưu log)
     └──────▶ Lưu trữ (quá 90 ngày không xử lý)
```

### Trạng thái Quan hệ
```
Đề xuất ──▶ Đã xác nhận
    └─────▶ Mâu thuẫn ──▶ (F16) ──▶ Đã xác nhận / Bác bỏ
```

### Trạng thái đơn tư vấn / biên tập
```
Lead ▶ Đang tư vấn ▶ Đã báo giá ▶ Đã chốt ▶ Đang biên tập
     ▶ Chờ gia đình duyệt ▶ Đã kích hoạt ▶ Đã bàn giao ▶ Đóng
```

Đơn khách tự mua (F11) bắt đầu ở **Chưa thanh toán**, không đi qua Lead.

### Trạng thái đơn sản xuất bảng QR
```
Chờ duyệt mẫu ▶ Đang sản xuất ▶ Kiểm tra QR ▶ Đóng gói ▶ Vận chuyển ▶ Đã giao
```

---

## PHỤ LỤC B — Danh sách màn hình cần thiết kế UI (MVP)

| # | Màn hình | Nền tảng | Độ ưu tiên thiết kế |
|---|---|---|---|
| 1 | Trang tưởng niệm công khai (5 tab) | Mobile + Desktop | ⭐⭐⭐ Cao nhất |
| 2 | Tạo nhanh + xem trước theo mẫu | Mobile + Desktop | ⭐⭐⭐ |
| 3 | Chỉnh sửa nâng cao (7 nhóm, không chặn xem trước) | Desktop | ⭐⭐⭐ |
| 4 | Chọn gói, nâng gói và thanh toán | Mobile + Desktop | ⭐⭐⭐ |
| 5 | Tùy chọn bảng QR và duyệt mẫu | Mobile + Desktop | ⭐⭐ |
| 6 | Địa chỉ nhận hàng | Mobile + Desktop | ⭐⭐ |
| 7 | Theo dõi đơn | Mobile + Desktop | ⭐⭐ |
| 8 | Bảng điều khiển gia đình | Mobile + Desktop | ⭐⭐ |
| 9 | Kho tư liệu | Desktop + Mobile | ⭐⭐ |
| 10 | Xem trước và duyệt | Desktop | ⭐⭐ |
| 11 | Form "Gửi một kỷ niệm" | Mobile | ⭐⭐ |
| 12 | Mời người thân, người quản lý dự phòng | Mobile + Desktop | ⭐ |
| 13 | Trang giới thiệu + bảng gói | Desktop + Mobile | ⭐⭐ |
| 14 | Đăng ký/đăng nhập OTP | Mobile | ⭐ |
| 15 | Quản trị vận hành (đơn, sản xuất bảng) | Desktop | ⭐ |

*(Đã có mockup cho trang tưởng niệm (#1, ảnh 01 và 20) và màn chỉnh sửa nâng cao (#3, ảnh 21). Chưa có mockup tạo nhanh, chọn gói và thanh toán.)*

---

**Tài liệu liên quan:**
- [00 — Tổng quan & Đối tượng sử dụng](./00-TONG-QUAN-VA-DOI-TUONG-SU-DUNG.md)
- [01 — Danh mục chức năng Web & App](./01-DANH-MUC-CHUC-NANG.md)
