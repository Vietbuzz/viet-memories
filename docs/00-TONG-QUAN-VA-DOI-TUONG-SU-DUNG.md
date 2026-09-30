# KÝ ỨC VIỆT — TÀI LIỆU THIẾT KẾ CHỨC NĂNG
## Phần 0: Tổng quan sản phẩm & Đối tượng sử dụng

> Phiên bản: 0.1 (bản cơ sở để thống nhất) — Ngày: 30/09/2026
> Nguồn: tổng hợp từ 15 tài liệu/infographic chiến lược trong thư mục dự án.
> Trạng thái: **ĐỀ XUẤT — cần chốt trước khi sang thiết kế chi tiết.**

---

## 1. Tóm tắt sản phẩm

**Ký Ức Việt** là nền tảng **di sản gia đình số** cho người Việt: lưu giữ câu chuyện một đời người, kết nối nhiều thế hệ.

**Bài toán:**
- Thông tin gia đình nằm rải rác, không có nơi tập trung.
- Ảnh cũ và ký ức dễ thất lạc theo thời gian, đặc biệt khi người giữ chuyện không còn.
- Gia phả giấy khó cập nhật, khó tra cứu, dễ mất.
- Bia mộ chỉ lưu được thông tin tối thiểu (tên, năm sinh, năm mất).

**Giải pháp cốt lõi — chuỗi 4 mắt xích:**

```
Mã QR  →  Trang tưởng niệm  →  Gia phả số  →  Bản đồ phần mộ
(cửa vào)   (sản phẩm lõi)      (mở rộng)      (B2B)
```

**Ba nguyên lý nền tảng:**
1. **QR là cửa truy cập** — không phải nơi chứa dữ liệu. Dữ liệu, câu chuyện và quan hệ gia đình mới là tài sản cốt lõi, lưu trên nền tảng.
2. **Hồ sơ là sản phẩm** — mỗi hồ sơ một người đã khuất là một đơn vị bán hàng, một đơn vị quản lý quyền, một đơn vị dữ liệu.
3. **Niềm tin là nền tảng** — gia đình kiểm soát nội dung; mọi thay đổi có nhật ký; AI chỉ xử lý tư liệu gia đình cung cấp, không tự tạo dữ kiện.

---

## 2. Quyết định về nền tảng kỹ thuật (đề xuất chốt)

| Hạng mục | Đề xuất | Lý do |
|---|---|---|
| **Giai đoạn 1** | **Web responsive / PWA** — chưa làm app native | Điểm vào chính là quét QR → mở trình duyệt. Người viếng mộ không cài app. Rút ngắn thời gian ra thị trường. |
| **Giai đoạn 2** | Bổ sung app native (iOS/Android) nếu có nhu cầu thật | Chỉ khi cần: thông báo đẩy nhắc giỗ, quay/ghi âm ký ức tại chỗ, xem offline. |
| **Ưu tiên giao diện** | **Mobile-first** cho trang tưởng niệm; **Desktop-first** cho khu vực biên tập & quản trị | Người xem dùng điện thoại; người tạo hồ sơ và admin dùng máy tính. |

> **Hệ quả cho tài liệu này:** mọi mô tả "app" bên dưới hiểu là **PWA/web trên điện thoại**, trừ khi ghi rõ "app native (GĐ2)".

---

## 3. Bốn mảng kinh doanh (phạm vi chức năng)

| # | Mảng | Ưu tiên | Khách hàng | Sản phẩm |
|---|---|---|---|---|
| 01 | **Trang tưởng niệm & QR** | Ưu tiên ban đầu | Gia đình; đối tác bia mộ, đá mỹ nghệ | Hồ sơ tưởng niệm, ảnh, tiểu sử, album; QR khắc trên vật liệu bền |
| 02 | **Gia phả & dòng họ** | Mở rộng theo nhu cầu | Gia đình, dòng họ, ban quản lý nhà thờ họ | Cây gia phả, hồ sơ thành viên, quan hệ, nhánh họ |
| 03 | **Nội dung & kho ký ức** | Ưu tiên ban đầu | Gia đình muốn lưu chuyện đời, ảnh cũ, tư liệu | Tiểu sử, album số, dòng thời gian, ghi âm, video ký ức |
| 04 | **Nghĩa trang & vị trí mộ** | B2B — thử khi có đối tác | Ban quản lý nghĩa trang; khu mộ dòng họ | Sơ đồ khu–lô–hàng–mộ, tọa độ, tìm kiếm, chỉ dẫn, lịch chăm sóc |

**Lộ trình sản phẩm đề xuất:** 01 + 03 (bán ngay) → 02 (khi gia đình chủ động thêm quan hệ) → 04 (khi có đối tác B2B trả phí).

---

## 4. Đối tượng sử dụng

### 4.1. Bốn nhóm khách hàng chính

#### Nhóm 1 — GIA ĐÌNH *(ưu tiên số 1)*
| Vai trò trong nhóm | Mô tả |
|---|---|
| **Người mua** | Con cháu đứng ra tổ chức (thường 30–55 tuổi, ở thành phố, có thu nhập) |
| **Người góp tư liệu** | Người lớn tuổi và họ hàng — giữ ảnh cũ, biết chuyện xưa |
| **Người duyệt** | Đại diện được gia đình thống nhất (người quản lý hồ sơ) |
| **Dịp phát sinh nhu cầu** | Làm/sửa bia mộ, ngày giỗ, tu sửa khu mộ, chuẩn bị bị ốm, họp mặt gia đình |
| **Họ cần thấy** | Hồ sơ mẫu đẹp, dễ dùng, điều kiện duy trì rõ ràng |

#### Nhóm 2 — DÒNG HỌ
| Vai trò | Mô tả |
|---|---|
| **Người mua** | Đại diện hoặc ban liên lạc dòng họ |
| **Người góp** | Các nhánh họ |
| **Người duyệt** | Người quản trị được dòng họ thống nhất |
| **Nhu cầu** | Số hóa gia phả, tìm tổ tiên, lưu tư liệu, quản lý đóng góp |
| **Họ cần thấy** | Quan hệ chính xác, quyền sửa rõ ràng, xuất dữ liệu được |

#### Nhóm 3 — ĐỐI TÁC GIỚI THIỆU *(kênh phân phối, không phải người dùng cuối)*
- **Ai:** cơ sở bia mộ, đá mỹ nghệ, dịch vụ tang lễ.
- **Vai trò:** giới thiệu gia đình và phối hợp gắn QR vật lý.
- **Nhu cầu:** dễ giới thiệu, bàn giao ổn định, đối soát hoa hồng minh bạch.
- **Ràng buộc quan trọng:** **không tự sở hữu dữ liệu gia đình.**

#### Nhóm 4 — BAN QUẢN LÝ NGHĨA TRANG *(B2B, giai đoạn sau)*
- **Người mua:** đơn vị có thẩm quyền và ngân sách.
- **Người dùng:** nhân viên quản lý, chăm sóc và tra cứu.
- **Nhu cầu:** tìm mộ, cập nhật hồ sơ, theo dõi công việc chăm sóc.
- **Họ cần thấy:** dữ liệu vị trí đúng, giảm việc quản lý thủ công.

### 4.2. Người dùng ẩn danh — QUAN TRỌNG NHẤT VỀ SỐ LƯỢNG
**Người quét QR tại mộ / người được chia sẻ link.** Không có tài khoản, không đăng nhập. Đây là nhóm tạo hiệu ứng lan truyền (vòng tăng trưởng). Trải nghiệm của họ phải:
- Mở được ngay trên điện thoại, không cần cài gì, không cần đăng nhập.
- Chỉ thấy phần gia đình cho phép công khai.
- Có lối vào rõ ràng để **"Gửi một kỷ niệm"** hoặc **"Đề nghị kết nối"** → chính là đầu vào của hồ sơ mới.

### 4.3. Người vận hành nội bộ
Hiện tại: **2 người điều hành (founder) + 8 vai trò chuyên môn** (A1–A8) chia việc, có AI hỗ trợ theo từng công việc.

| Mã | Phòng ban / Vai trò | Phụ trách | Chức năng hệ thống liên quan |
|---|---|---|---|
| A1 | Điều phối & chiến lược | Cả hai founder | Bảng việc chung, báo cáo |
| A2 | Nghiên cứu & tăng trưởng | Partner | Danh sách lead, nội dung tiếp thị |
| A3 | Kinh doanh & đối tác | Partner | CRM, báo giá, checklist đơn, hợp đồng đối tác |
| A4 | Nội dung & di sản | Bạn (founder SP) | Công cụ biên tập hồ sơ, phân loại ảnh, chép lời kể |
| A5 | Sản phẩm & công nghệ | Bạn | Phát hành, sao lưu, khôi phục |
| A6 | Vận hành & khách hàng | Partner | Ticket, lịch giao, phối hợp QR, hướng dẫn |
| A7 | Tài chính & hành chính | Founder ngân sách | Thu chi, đối soát, hoa hồng |
| A8 | Dữ liệu & kiểm soát chất lượng | Bạn | Checklist xuất bản, nhật ký sự cố, soát quyền |

> **Lưu ý:** đây là *vai trò*, không phải 8 nhân sự. Hệ thống cần **phân quyền theo vai trò**, một người có thể giữ nhiều vai.

---

## 5. Ma trận vai trò & quyền (RBAC đề xuất)

| Vai trò | Xem công khai | Xem nội dung Gia đình | Xem nội dung Riêng tư | Gửi đóng góp | Sửa hồ sơ | Duyệt & xuất bản | Cấp quyền | Xuất dữ liệu | Xóa |
|---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Khách ẩn danh (quét QR) | ✅ | ❌ | ❌ | ✅* | ❌ | ❌ | ❌ | ❌ | ❌ |
| Thành viên gia đình | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Người đóng góp (được mời) | ✅ | ✅ | ❌ | ✅ | ✅ (bản nháp) | ❌ | ❌ | ❌ | ❌ |
| **Người quản lý gia đình** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ (trong hồ sơ) | ✅ (yêu cầu) | ⚠️ (yêu cầu) |
| Quản trị dòng họ | ✅ | ✅ (nhánh được giao) | ❌ | ✅ | ✅ | ✅ (dữ liệu gia phả) | ✅ (nhánh) | ✅ | ❌ |
| Đối tác giới thiệu | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Nhân viên nghĩa trang | ✅ | ❌ | ❌ | ❌ | ✅ (chỉ dữ liệu mộ) | ❌ | ❌ | ✅ (dữ liệu mộ) | ❌ |
| Vận hành nội bộ (A4/A6) | ✅ | ✅ (khi được giao đơn) | ⚠️ (chỉ phần cần làm, có nhật ký) | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ |
| Quản trị hệ thống (A5/A8) | ✅ | ✅ | ✅ (có nhật ký) | — | ✅ | ✅ | ✅ | ✅ | ✅ |
| AI / tự động | — | ⚠️ (chỉ phần cần làm) | ❌ | — | ✅ (đề xuất) | ❌ | ❌ | ❌ | ❌ |

`*` Khách ẩn danh gửi đóng góp phải để lại tên + liên hệ, nội dung vào hàng chờ duyệt.

**Bốn quy tắc bất biến:**
1. **Quét QR không tự cấp quyền xem tư liệu riêng.**
2. **AI không tự công bố** — mọi nội dung AI sinh ra chỉ là đề xuất, phải qua người thật duyệt.
3. **Người đóng góp không được ghi đè dữ kiện đã duyệt** — chỉ đề nghị sửa.
4. **Chi tiền, ký kết, đăng, đổi quyền, xóa: chỉ người thật duyệt.**

---

## 6. Ba mức hiển thị nội dung

| Mức | Ai xem được | Nội dung điển hình |
|---|---|---|
| 🌐 **Công khai** | Bất kỳ ai có link/QR | Họ tên, ảnh chân dung, năm sinh–năm mất, lời giới thiệu ngắn, một phần câu chuyện (do gia đình chủ động chọn) |
| 👨‍👩‍👧 **Gia đình** | Thành viên đã được cấp quyền | Album đầy đủ, gia phả, câu chuyện chi tiết, ghi âm, video |
| 🔒 **Riêng tư** | Chỉ người được chỉ định | Giấy tờ, thông tin liên hệ, dữ liệu quản lý mộ, thông tin quản trị |

**Quy tắc mặc định:** trường nào chưa chọn mức → mặc định **Riêng tư**. Gia đình phải chủ động mở ra.

---

## 7. Mô hình dữ liệu cốt lõi (5 thực thể phải quản lý)

```
┌─────────────┐      ┌─────────────┐      ┌─────────────┐
│  HỒ SƠ NGƯỜI │─────▶│   QUAN HỆ    │◀─────│ HỒ SƠ NGƯỜI │
│  (Person)    │      │ (Relation)   │      │  (Person)   │
└──────┬───────┘      └─────────────┘      └─────────────┘
       │
       ├──▶ ┌──────────────┐   Ảnh, ghi âm, video, tài liệu
       │    │   TƯ LIỆU     │   + bản gốc, người đóng góp, quyền sử dụng
       │    │   (Asset)     │
       │    └──────────────┘
       │
       ├──▶ ┌──────────────┐   Nghĩa trang, khu–lô–hàng, mã mộ,
       │    │  VỊ TRÍ MỘ    │   tọa độ đã kiểm tra
       │    │   (Grave)     │
       │    └──────────────┘
       │
       └──▶ ┌──────────────┐   Ai sửa, sửa gì, lúc nào, ai duyệt
            │ LỊCH SỬ THAY  │   + có phiên bản, khôi phục được
            │ ĐỔI (Audit)   │
            └──────────────┘
```

| Thực thể | Trường bắt buộc | Ghi chú thiết kế |
|---|---|---|
| **Hồ sơ người** | Họ tên, năm sinh, năm mất, người quản lý | Cho phép **để trống hoặc đánh dấu "chờ xác nhận"** khi chưa rõ ngày/tháng — không ép nhập đủ |
| **Quan hệ** | Loại (cha/mẹ/con/vợ/chồng/anh chị em), 2 đầu, người xác nhận, trạng thái kiểm chứng | Trạng thái: `đề xuất` / `đã xác nhận` / `mâu thuẫn` |
| **Tư liệu** | File, loại, nguồn, người đóng góp, quyền sử dụng, mức hiển thị | **Luôn giữ bản gốc**, bản chỉnh sửa là phiên bản mới |
| **Vị trí mộ** | Nghĩa trang, khu–lô–hàng–mộ, mã mộ, tọa độ, trạng thái kiểm tra | Tọa độ phải có cờ "đã kiểm tra thực địa" |
| **Lịch sử thay đổi** | Ai, cái gì, khi nào, ai duyệt, phiên bản trước | Bất biến — không được xóa |

**Xử lý dữ liệu mâu thuẫn (quy tắc chốt):**
```
Phát hiện mâu thuẫn → Gắn nhãn "CHỜ XÁC NHẬN"
                    → Giữ nguyên cả hai nguồn + lịch sử
                    → Đại diện có thẩm quyền quyết định
```
❌ **Không tự động gộp hồ sơ chỉ vì trùng tên.**

---

## 8. Cam kết vận hành lâu dài (phải có trong sản phẩm)

| Cam kết | Yêu cầu chức năng |
|---|---|
| **Thời hạn rõ** | Mỗi hồ sơ hiển thị: thời gian lưu, dung lượng, phí duy trì, cách gia hạn |
| **Sao lưu thực** | Lịch sao lưu + kiểm tra khôi phục định kỳ; giữ bản gốc tư liệu |
| **Chuyển người quản lý** | Quy trình xác minh khi người phụ trách không còn khả năng quản lý |
| **Rời dịch vụ** | Xuất toàn bộ dữ liệu (định dạng mở), thông báo và bàn giao nếu ngừng hoạt động |

> ⚠️ **Không hứa lưu trữ vĩnh viễn khi chưa có nguồn lực bảo đảm.** Ngôn ngữ giao diện phải phản ánh đúng cam kết thực tế.

---

## 9. Vòng tăng trưởng (thiết kế sản phẩm phải phục vụ vòng này)

```
       QR được quét
            ↓
  Xem trang tưởng niệm
            ↓
     Mời người thân  ←──────────┐
            ↓                    │
   Bổ sung ký ức/tư liệu         │
            ↓                    │
      Thêm tổ tiên               │
            ↓                    │
  Tạo hồ sơ mới ─────────────────┘
```
Mỗi bước trong vòng này phải có **một nút CTA rõ ràng trên giao diện**. Đây là tiêu chí thiết kế UI quan trọng nhất.

---

## 10. Chỉ số kiểm chứng (KPI gắn với chức năng)

| KPI | Mục tiêu | Chức năng cần đo |
|---|---|---|
| Tỷ lệ hoàn tất hồ sơ | ≥ 60% | Theo dõi điểm bỏ dở trong wizard 7 bước |
| Người thân được mời / hồ sơ | ≥ 2 | Đếm lời mời gửi + chấp nhận |
| Hồ sơ có đóng góp từ người thứ hai | ≥ 30% | Đếm đóng góp được duyệt |
| Đối tác tiếp tục phân phối | ≥ 3 | Dashboard đối tác |
| Thời gian hoàn tất / hồ sơ | Theo dõi | Timestamp từng bước quy trình |

---

## 11. Những điểm CẦN CHỐT trước khi sang thiết kế chi tiết

| # | Câu hỏi | Ảnh hưởng |
|---|---|---|
| 1 | Xác nhận **Web/PWA trước, chưa làm app native** — đúng không? | Quyết định toàn bộ kiến trúc frontend |
| 2 | Phạm vi MVP: chỉ **mảng 01 + 03** (hồ sơ + QR + kho ký ức), hay kèm **gia phả cơ bản**? | Chênh lệch ~40% khối lượng |
| 3 | Gia đình **tự tạo hồ sơ (self-serve)** hay **đội vận hành làm hộ (dịch vụ)** — hay cả hai? | Quyết định có cần wizard công khai hay chỉ cần back-office |
| 4 | Có làm **tài khoản miễn phí + hồ sơ Basic miễn phí** ngay từ MVP không? | Ảnh hưởng đăng ký, chống lạm dụng, chi phí lưu trữ |
| 5 | QR vật lý: nền tảng **tự sản xuất** hay **đối tác đá mỹ nghệ làm**? | Quyết định module quản lý sản xuất & bàn giao |
| 6 | Mảng 04 (nghĩa trang) có nằm trong **cùng một hệ thống** hay là **sản phẩm tách riêng**? | Quyết định kiến trúc đa tenant |
| 7 | Cần **đa ngôn ngữ (Việt/Anh)** ngay không? (tài liệu có nhắc "bản song ngữ") | Ảnh hưởng cấu trúc nội dung từ đầu |
| 8 | **Lịch âm & nhắc giỗ** — MVP hay giai đoạn sau? | Cần thư viện lịch âm + hệ thống thông báo |

---

**Tài liệu liên quan:**
- [01 — Danh mục chức năng Web & App](./01-DANH-MUC-CHUC-NANG.md)
- [02 — Flow chức năng chi tiết](./02-FLOW-CHUC-NANG-CHI-TIET.md)
