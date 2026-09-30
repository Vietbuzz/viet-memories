# KÝ ỨC VIỆT — TÀI LIỆU THIẾT KẾ CHỨC NĂNG
## Phần 2: Flow chức năng chi tiết

> Phiên bản 0.1 — Bản cơ sở để thống nhất
> Mỗi flow gồm: **Ai làm · Điều kiện vào · Các bước · Trạng thái dữ liệu · Ngoại lệ · Điểm đo**

---

## MỤC LỤC

**Nhóm 1 — Flow người dùng cuối**
- [F1. Quét QR → xem trang tưởng niệm (khách ẩn danh)](#f1)
- [F2. Khách gửi một kỷ niệm](#f2)
- [F3. Đăng ký & tạo không gian gia đình](#f3)
- [F4. Tạo hồ sơ tưởng niệm — wizard 7 bước](#f4)
- [F5. Mời người thân & cấp quyền](#f5)
- [F6. Người thân đóng góp tư liệu](#f6)
- [F7. Duyệt nội dung & xuất bản](#f7)
- [F8. Mở rộng từ hồ sơ → cây gia phả](#f8)
- [F9. Chuyển giao người quản lý](#f9)
- [F10. Gia hạn / xuất dữ liệu / rời dịch vụ](#f10)

**Nhóm 2 — Flow kinh doanh & vận hành**
- [F11. Hành trình khách hàng 6 bước (end-to-end)](#f11)
- [F12. Từ lead đến đơn hàng](#f12)
- [F13. Quy trình sản xuất một đơn (7 bước nội bộ)](#f13)
- [F14. Sản xuất & bàn giao QR vật lý](#f14)
- [F15. Đối tác giới thiệu & đối soát hoa hồng](#f15)

**Nhóm 3 — Flow hệ thống**
- [F16. Xử lý dữ liệu mâu thuẫn / trùng lặp](#f16)
- [F17. Quy tắc AI trong quy trình](#f17)

---
---

# NHÓM 1 — FLOW NGƯỜI DÙNG CUỐI

<a id="f1"></a>
## F1. Quét QR → xem trang tưởng niệm

**Ai:** Khách ẩn danh (người viếng mộ, người được chia sẻ link)
**Điều kiện vào:** Hồ sơ đã ở trạng thái `Đã xuất bản`
**Nền tảng:** Mobile (99% trường hợp)

### Các bước
```
1. Quét QR trên bia mộ / bảng mica / bảng kim loại
        ↓
2. Trình duyệt mở kyucviet.vn/h/{ma-ho-so}
        ↓
3. Hiển thị ngay khối đầu trang:
   ảnh chân dung · tên · năm sinh–năm mất · câu trích dẫn
        ↓
4. Người xem cuộn/chuyển tab:
   Câu chuyện → Dấu mốc → Album → Người thân → Nơi an nghỉ
        ↓
5. Ba lối rẽ CTA (luôn hiện):
   ┌─ [Chia sẻ] ──────→ Zalo / FB / sao chép link
   ├─ [Gửi một kỷ niệm] → F2
   └─ [Tôi là người thân] → F5 (yêu cầu kết nối)
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
| Hồ sơ chưa xuất bản | Trang "Hồ sơ đang được gia đình hoàn thiện" + nút Liên hệ |
| Hồ sơ đã gỡ / hết hạn | Trang "Hồ sơ tạm ngừng hiển thị" + hướng dẫn liên hệ người quản lý |
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
## F4. Tạo hồ sơ tưởng niệm — WIZARD 7 BƯỚC ⭐

**Ai:** Người quản lý gia đình, hoặc A4 (biên tập viên) làm hộ
**Nền tảng:** Desktop-first, có bản mobile rút gọn
**Bố cục màn hình:** Danh sách bước (trái) · Form (giữa) · **Xem trước trực tiếp (phải)**

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
- Mỗi người: **liên kết hồ sơ đã có** hoặc **tạo hồ sơ tối giản** (chỉ tên + năm)
- Hệ thống cảnh báo nếu phát hiện hồ sơ trùng → F16
- 🔗 Đây là **cầu nối sang gia phả** (F8)

### Bước 5 — Nơi an nghỉ
- Nghĩa trang / địa điểm · Khu – Lô – Hàng – Mộ · Tọa độ (chọn trên bản đồ) · Ảnh khu mộ
- **Ngày giỗ âm lịch** (vd: 18 tháng Ba âm lịch) — hệ thống tự quy đổi sang dương lịch hằng năm
- Ghi chú đường đi

### Bước 6 — Quyền hiển thị
Bảng đặt mức cho từng khối:

| Khối nội dung | Công khai | Gia đình | Riêng tư |
|---|:--:|:--:|:--:|
| Tên, ảnh, năm sinh–mất | ◉ | ○ | ○ |
| Lời giới thiệu ngắn | ◉ | ○ | ○ |
| Câu chuyện cuộc đời | ○ | ◉ | ○ |
| Album ảnh | ○ | ◉ | ○ |
| Người thân | ◉ | ○ | ○ |
| Nơi an nghỉ | ○ | ◉ | ○ |
| Giấy tờ, liên hệ | ○ | ○ | ◉ |

⚠️ Cảnh báo hiển thị cố định: **"Quét QR không tự cấp quyền xem tư liệu riêng."**

### Bước 7 — Kiểm tra & hoàn tất
Checklist bắt buộc tick đủ:
- ☐ Xác nhận tên và ngày tháng
- ☐ Kiểm tra quyền hiển thị
- ☐ Gia đình duyệt nội dung

→ Nút **[Gửi gia đình duyệt]**

### Trạng thái dữ liệu
```
Nháp ──[Gửi duyệt]──▶ Chờ gia đình duyệt ──[Duyệt]──▶ Sẵn sàng xuất bản
  ▲                            │                              │
  └────[Yêu cầu sửa]───────────┘                    [Xuất bản]│
                                                               ▼
                                                        Đã xuất bản
```

### Ngoại lệ
| Tình huống | Xử lý |
|---|---|
| Mất mạng giữa chừng | Tự lưu nháp cục bộ, đồng bộ khi có mạng lại |
| Bỏ dở nhiều ngày | Nhắc qua Zalo/email sau 3 ngày và 7 ngày, kèm link quay lại đúng bước đang dở |
| Nhiều người cùng sửa | Khóa mềm theo bước + cảnh báo "A đang sửa bước này" |
| Không có ảnh chân dung | Dùng ảnh mặc định trang nhã, vẫn xuất bản được |

### Điểm đo ⭐
**Tỷ lệ hoàn tất hồ sơ — mục tiêu ≥ 60%.** Đo điểm bỏ dở theo từng bước (1→7) để biết bước nào gây nghẽn.

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

Hướng B — Yêu cầu từ ngoài vào:
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
4. Khi hồ sơ đã sẵn sàng → [Xuất bản]
        ↓
5. Hệ thống:
   • Sinh URL công khai ổn định: kyucviet.vn/h/{ma}
   • Kích hoạt mã QR gắn với URL đó
   • Ghi phiên bản xuất bản + timestamp + người duyệt
   • Thông báo cho toàn bộ thành viên gia đình
```

### Quy tắc bất biến
1. **Mọi nội dung AI sinh ra phải qua bước duyệt của người thật** trước khi hiển thị công khai.
2. **URL công khai không bao giờ đổi** sau lần xuất bản đầu.
3. **Lịch sử thay đổi không được xóa** — chỉ thêm.
4. Gỡ xuất bản chỉ ẩn khỏi công khai, **không xóa dữ liệu**.

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
4. Mỗi người mới thêm = một hồ sơ tối giản (tên + năm)
   → có thể nâng cấp thành hồ sơ đầy đủ bất kỳ lúc nào
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

**Bắt buộc từ MVP:** mỗi hồ sơ phải khai **người quản lý dự phòng**.

---

<a id="f10"></a>
## F10. Gia hạn / Xuất dữ liệu / Rời dịch vụ

```
GIA HẠN
1. Hệ thống nhắc trước 60 / 30 / 7 ngày (Zalo + email + banner trong app)
2. Hiển thị rõ: hết hạn khi nào · phí bao nhiêu · nếu không gia hạn thì sao
3. Thanh toán → gia hạn ngay
4. Nếu quá hạn:
   • Ngày 1–30:  vẫn hiển thị, có banner nhắc
   • Ngày 31–90: chuyển sang chế độ chỉ đọc, banner rõ ràng
   • Sau 90 ngày: ẩn khỏi công khai, DỮ LIỆU VẪN GIỮ
   • Không bao giờ tự xóa dữ liệu vì quá hạn mà chưa báo

XUẤT DỮ LIỆU  (quyền của gia đình, luôn có)
1. Cài đặt → [Xuất dữ liệu]
2. Chọn phạm vi: một hồ sơ / cả không gian gia đình
3. Hệ thống đóng gói: ảnh & tư liệu bản gốc + JSON dữ liệu + PDF trang tưởng niệm
4. Gửi link tải (có hạn 7 ngày) qua email

RỜI DỊCH VỤ
1. Yêu cầu ngừng → bắt buộc xuất dữ liệu trước
2. Xác nhận 2 lần, cách nhau 7 ngày
3. Gỡ công khai + vô hiệu QR
4. Giữ dữ liệu thêm 90 ngày (cho phép khôi phục) rồi mới xóa
```

> ⚠️ **Nguyên tắc truyền thông:** không dùng từ "vĩnh viễn" trong giao diện khi chưa có nguồn lực bảo đảm. Dùng: *"lưu trữ trong thời hạn dịch vụ, có phương án xuất dữ liệu và kế thừa."*

---
---

# NHÓM 2 — FLOW KINH DOANH & VẬN HÀNH

<a id="f11"></a>
## F11. Hành trình khách hàng 6 bước (end-to-end) ⭐

```
┌─1─────────────┐  ┌─2─────────────┐  ┌─3─────────────┐
│ BIẾT ĐẾN &    │→ │ CHỌN GÓI &    │→ │ GỬI TƯ LIỆU   │
│ XEM MẪU       │  │ THỐNG NHẤT    │  │               │
│               │  │               │  │               │
│ Đối tác giới  │  │ Chốt phạm vi, │  │ Ảnh, lời kể,  │
│ thiệu hoặc    │  │ giá, thời     │  │ thông tin;    │
│ nội dung; xem │  │ gian, duy trì │  │ chọn quyền    │
│ 1 hồ sơ mẫu   │  │ và người      │  │ hiển thị;     │
│ hoàn chỉnh    │  │ quản lý       │  │ kiểm phần     │
│               │  │               │  │ còn thiếu     │
└───────────────┘  └───────────────┘  └───────────────┘
┌─4─────────────┐  ┌─5─────────────┐  ┌─6─────────────┐
│ XEM TRƯỚC &   │→ │ NHẬN HỒ SƠ &  │→ │ BỔ SUNG &     │
│ DUYỆT         │  │ QR            │  │ KẾT NỐI       │
│               │  │               │  │               │
│ Gia đình xác  │  │ Kiểm tra quét │  │ Mời người     │
│ nhận tên,     │  │ bằng điện     │  │ thân, thêm ký │
│ ngày, quan hệ;│  │ thoại; nhận   │  │ ức; chỉ nâng  │
│ yêu cầu sửa   │  │ hướng dẫn và  │  │ cấp khi có    │
│ trước khi đăng│  │ quyền quản lý │  │ nhu cầu       │
└───────────────┘  └───────────────┘  └───────────────┘
```

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
## F13. Quy trình sản xuất một đơn (7 bước nội bộ) ⭐

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
   └ Soát điều kiện xuất bản
        ↓
4. GIA ĐÌNH XÁC NHẬN
   ├ Sửa tên, ngày, quan hệ
   └ DUYỆT BẢN CUỐI              ← cổng bắt buộc
        ↓
5. FOUNDER DUYỆT · A5 PHÁT HÀNH
   ├ Xuất bản hồ sơ
   └ Sinh & liên kết QR ổn định
        ↓
6. A6 BÀN GIAO
   ├ Quét thử QR bằng điện thoại thật
   ├ Hướng dẫn gia đình sử dụng
   ├ CHUYỂN QUYỀN QUẢN LÝ cho gia đình
   └ Nghiệm thu
        ↓
7. A7 ĐỐI SOÁT · A1 TỔNG HỢP
   ├ Thu chi, hoa hồng đối tác
   └ Ghi lỗi và bài học
```

### ✅ Điều kiện "HOÀN TẤT" một đơn (checklist nghiệm thu)
- ☐ Nội dung được gia đình duyệt
- ☐ QR mở đúng trang (đã quét thử bằng điện thoại thật)
- ☐ Quyền truy cập đúng như đã thống nhất
- ☐ Khách nhận hướng dẫn sử dụng
- ☐ Lưu biên bản nghiệm thu

### Yêu cầu hệ thống
- Mỗi đơn có **một mã đơn xuyên suốt** cả 7 bước
- Mỗi bước có **một người chủ trì** và **một người duyệt**
- Theo dõi **đúng hẹn** và **công hỗ trợ sau giao**

---

<a id="f14"></a>
## F14. Sản xuất & bàn giao QR vật lý

```
1. Hồ sơ xuất bản → sinh URL ổn định → sinh mã QR
        ↓
2. Chọn sản phẩm: Bảng mica | Bảng kim loại | Khắc trực tiếp lên đá | Bảng bổ sung
        ↓
3. Thiết kế bảng (logo, tên, câu chữ) → gia đình duyệt mẫu
        ↓
4. Đặt sản xuất (nội bộ hoặc đối tác đá mỹ nghệ)
   Trạng thái: Đặt → Đang sản xuất → Đã xong → Vận chuyển → Lắp đặt
        ↓
5. Lắp đặt tại mộ / bàn giao để gia đình tự đặt trong nhà
        ↓
6. ⭐ QUÉT THỬ BẰNG ĐIỆN THOẠI THẬT TẠI HIỆN TRƯỜNG
   ├ Mở đúng trang?
   ├ Tốc độ chấp nhận được với 4G tại chỗ?
   └ Hiển thị đúng nội dung công khai?
        ↓
7. Chụp ảnh nghiệm thu → lưu vào hồ sơ đơn → đóng đơn
```

### Ngoại lệ
| Tình huống | Xử lý |
|---|---|
| QR mờ, khó quét | Làm lại, chi phí tính vào lỗi sản xuất; ghi vào nhật ký sự cố (A8) |
| Bảng hỏng/mất sau này | Cấp lại bảng, **giữ nguyên URL cũ** — không sinh mã mới |
| Gia đình đổi gói | URL không đổi |

---

<a id="f15"></a>
## F15. Đối tác giới thiệu & đối soát hoa hồng *(P1)*

```
1. A3 ký chính sách đối tác: nguồn đơn, trách nhiệm, hoa hồng, cách đối soát
        ↓
2. Cấp cho đối tác: mã giới thiệu riêng + bộ công cụ
   ├ Một hồ sơ mẫu hoàn chỉnh + QR thử thật
   ├ Bảng gói dịch vụ (phạm vi, thời gian, điều kiện duy trì)
   └ Mẫu email/Zalo giới thiệu
        ↓
3. Đối tác giới thiệu gia đình → đơn gắn mã nguồn
        ↓
4. Đơn hoàn tất → hệ thống tính hoa hồng
        ↓
5. A7 đối soát định kỳ → thanh toán
        ↓
6. Đánh giá: đối tác có đơn lặp lại không? (KPI: ≥ 3 đối tác tiếp tục)
```

> 🔒 **Ranh giới cứng:** đối tác **không truy cập được dữ liệu gia đình**. Cổng đối tác chỉ hiển thị: đơn do mình giới thiệu, trạng thái, hoa hồng.

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

### Trạng thái Hồ sơ
```
Nháp ──▶ Chờ gia đình duyệt ──▶ Sẵn sàng xuất bản ──▶ Đã xuất bản
  ▲              │                                          │
  └──────────────┘                              ┌───────────┤
     (yêu cầu sửa)                              ▼           ▼
                                          Tạm ẩn      Quá hạn (chỉ đọc)
                                                            │
                                                            ▼
                                                    Lưu trữ (ẩn, giữ dữ liệu)
```

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

### Trạng thái Đơn hàng
```
Lead ▶ Đang tư vấn ▶ Đã báo giá ▶ Đã chốt ▶ Đang sản xuất
     ▶ Chờ gia đình duyệt ▶ Đã phát hành ▶ Đã bàn giao ▶ Đã đối soát ▶ Đóng
```

### Trạng thái QR vật lý
```
Chưa đặt ▶ Đã đặt ▶ Đang sản xuất ▶ Đã xong ▶ Vận chuyển ▶ Đã lắp ▶ Đã nghiệm thu
```

---

## PHỤ LỤC B — Danh sách màn hình cần thiết kế UI (MVP)

| # | Màn hình | Nền tảng | Độ ưu tiên thiết kế |
|---|---|---|---|
| 1 | Trang tưởng niệm công khai (5 tab) | Mobile + Desktop | ⭐⭐⭐ Cao nhất |
| 2 | Wizard chỉnh sửa hồ sơ (7 bước) | Desktop | ⭐⭐⭐ |
| 3 | Bảng điều khiển gia đình | Mobile + Desktop | ⭐⭐ |
| 4 | Kho tư liệu | Desktop + Mobile | ⭐⭐ |
| 5 | Xem trước & duyệt | Desktop | ⭐⭐ |
| 6 | Form "Gửi một kỷ niệm" | Mobile | ⭐⭐ |
| 7 | Mời người thân & quản lý quyền | Mobile + Desktop | ⭐ |
| 8 | Trang giới thiệu + bảng gói | Desktop + Mobile | ⭐⭐ |
| 9 | Đăng ký/đăng nhập OTP | Mobile | ⭐ |
| 10 | Quản trị vận hành (đơn, QR) | Desktop | ⭐ |

*(Đã có mockup sẵn cho: #1 desktop, #1 mobile, #2 desktop — trong các file ảnh 01, 20, 21.)*

---

**Tài liệu liên quan:**
- [00 — Tổng quan & Đối tượng sử dụng](./00-TONG-QUAN-VA-DOI-TUONG-SU-DUNG.md)
- [01 — Danh mục chức năng Web & App](./01-DANH-MUC-CHUC-NANG.md)
