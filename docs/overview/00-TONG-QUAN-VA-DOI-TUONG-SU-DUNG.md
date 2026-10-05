# KÝ ỨC VIỆT — TÀI LIỆU THIẾT KẾ CHỨC NĂNG
## Phần 0: Tổng quan sản phẩm & Đối tượng sử dụng

> Phiên bản: 0.2 — Ngày: 05/10/2026
> Nguồn: bản cơ sở 30/09/2026, đã nhập ý kiến cộng tác viên trong `docs/suggestions/`.
> Trạng thái: **ĐÃ CẬP NHẬT THEO GÓP Ý — các điểm còn mở nằm ở mục 11.**

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
| 01 | **Trang tưởng niệm & QR** | Ưu tiên ban đầu | Gia đình; đối tác bia mộ, đá mỹ nghệ | Hồ sơ tưởng niệm số (ảnh, tiểu sử, album, QR số). Bảng QR vật lý là tùy chọn, không đi kèm mọi hồ sơ |
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
- **Vai trò:** giới thiệu gia đình và, với cơ sở bia mộ, tự khắc đá theo báo giá của họ.
- **Nhu cầu:** dễ giới thiệu, bàn giao QR ổn định. Công ty thu phí nền tảng và cấp QR; đối tác bia mộ tự báo giá, tự thu tiền khắc đá. Hoa hồng chỉ khi có thỏa thuận riêng.
- **Ràng buộc quan trọng:** **không tự sở hữu dữ liệu gia đình.**

#### Nhóm 4 — BAN QUẢN LÝ NGHĨA TRANG *(B2B, giai đoạn sau)*
- **Người mua:** đơn vị có thẩm quyền và ngân sách.
- **Người dùng:** nhân viên quản lý, chăm sóc và tra cứu.
- **Nhu cầu:** tìm mộ, cập nhật hồ sơ, theo dõi công việc chăm sóc.
- **Họ cần thấy:** dữ liệu vị trí đúng, giảm việc quản lý thủ công.

### 4.2. Người dùng ẩn danh — QUAN TRỌNG NHẤT VỀ SỐ LƯỢNG
**Người quét QR tại mộ / người được chia sẻ link.** Không có tài khoản, không đăng nhập. Đây là nhóm tạo hiệu ứng lan truyền (vòng tăng trưởng). Trải nghiệm của họ phải:
- Mở được ngay trên điện thoại, không cần cài gì, không cần đăng nhập.
- Chỉ thấy phần gia đình cho phép công khai. Hồ sơ đã trả phí vẫn có thể giữ riêng tư.
- Có lối vào **"Gửi một kỷ niệm"** ngay từ MVP. **"Đề nghị kết nối"** để giai đoạn 2.

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

**Quy tắc mặc định:** trường nào chưa chọn mức → mặc định **Riêng tư**. Người quản lý chủ động chọn phần được công khai. Hồ sơ đã trả phí có thể giữ riêng tư sau khi kích hoạt.

**Người còn sống:** dữ liệu của người còn sống không mặc định công khai, kể cả khi họ xuất hiện trên cây gia phả hoặc tab người thân.

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
| **Hồ sơ người** | Họ tên, năm sinh, năm mất, người quản lý | Cho phép **để trống hoặc đánh dấu "chờ xác nhận"** khi chưa rõ ngày/tháng — không ép nhập đủ. Phân biệt **thành viên gia phả tối giản** (tên, năm, quan hệ — không phát sinh phí) với **hồ sơ tưởng niệm trả phí**. Thêm người vào cây không tự tạo đơn hàng |
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

**Mã hồ sơ và QR:** giữ nguyên khi chỉnh sửa nội dung, nâng gói hoặc chuyển người quản lý. Mã của hồ sơ đã xóa không được gán lại cho người khác.

---

## 8. Cam kết vận hành lâu dài (phải có trong sản phẩm)

| Cam kết | Yêu cầu chức năng |
|---|---|
| **Hồ sơ đã mua** | Thanh toán một lần, lưu trữ trọn đời theo phạm vi gói đã công bố. Không hiện ngày hết hạn. Không buộc gia hạn để xem lại ký ức |
| **Phạm vi gói** | Hiện gói đã mua, số ảnh, dung lượng đã dùng và quyền lợi. **Basic:** dưới 100.000đ/hồ sơ; tối đa 5 ảnh; tiểu sử; trình bày theo mẫu; đường dẫn chia sẻ và QR số |
| **Bản nháp chưa thanh toán** | Có thời hạn lưu, thời điểm bắt đầu tính, nhắc trước hạn và cách xử lý khi hết hạn. Số ngày cụ thể chưa chốt |
| **Nâng gói & mua thêm** | Nâng trên hồ sơ hiện có; giữ nội dung, đường dẫn và QR. Mua thêm bảng QR hoặc dịch vụ video không tạo hồ sơ mới |
| **Sao lưu thực** | Lịch sao lưu + kiểm tra khôi phục định kỳ; giữ bản gốc tư liệu |
| **Người quản lý dự phòng** | Mỗi hồ sơ có người quản lý dự phòng. Tiếp quản phải xác minh; MVP cho phép xử lý thủ công |
| **Rời dịch vụ** | Xuất toàn bộ dữ liệu (định dạng mở). Tạm ẩn không làm mất dữ liệu hay quyền lưu trữ đã mua. Tiếp nhận yêu cầu xóa ngay từ MVP; xóa tự động làm sau |

> Cam kết "trọn đời" gắn với **phạm vi gói đã công bố** (số ảnh, dung lượng, loại tư liệu), không phải dung lượng không giới hạn. Giao diện không dùng cụm "vĩnh viễn không điều kiện". Nếu ngừng vận hành, vẫn phải xuất và bàn giao dữ liệu.

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
| Tỷ lệ hoàn tất hồ sơ | ≥ 60% | Đo lối tạo nhanh và điểm bỏ dở trong chỉnh sửa nâng cao |
| Người thân được mời / hồ sơ | ≥ 2 | Đếm lời mời gửi + chấp nhận |
| Hồ sơ có đóng góp từ người thứ hai | ≥ 30% | Đếm đóng góp được duyệt |
| Đối tác tiếp tục phân phối | ≥ 3 | Dashboard đối tác |
| Thời gian hoàn tất / hồ sơ | Theo dõi | Timestamp từng bước quy trình |

---

## 11. Quyết định đã chốt và điểm còn mở

### Đã chốt theo góp ý cộng tác viên

| # | Quyết định |
|---|---|
| 1 | **Web/PWA trước.** App native là P2, chỉ làm khi có nhu cầu thật. |
| 2 | MVP là **mảng 01 + 03**: hồ sơ số, kho tư liệu, thanh toán, bảng QR khi khách mua. Cây gia phả đầy đủ (B5) và phần mềm nghĩa trang là giai đoạn sau. Trong hồ sơ vẫn khai được **thành viên gia phả tối giản**, không phát sinh phí. |
| 3 | **Cả hai lối tạo hồ sơ.** Tự tạo (tạo nhanh, xem trước, thanh toán) là P0. Dịch vụ biên tập ký ức là P1; giai đoạn đầu có thể nhận và làm thủ công. |
| 4 | **Không có hồ sơ Basic miễn phí.** Basic là gói trả phí dưới 100.000đ/hồ sơ, thanh toán một lần. Một tài khoản quản lý nhiều hồ sơ. |
| 5 | **Bảng QR do công ty sản xuất và giao** (mica, kim loại; gốm khi đã kiểm tra mẫu). Khách tự lắp. Công ty không khắc trực tiếp lên đá. Đối tác bia mộ tự báo giá và thu tiền khắc đá; công ty thu phí nền tảng và cấp QR. |
| 6 | **Nhắc giỗ âm lịch là P1**, không nằm trong MVP. |
| 7 | Phí tính **theo từng hồ sơ người đã khuất**. Bảng QR vật lý và dịch vụ video là mua thêm, không bắt buộc đi kèm mọi hồ sơ. |
| 8 | Bốn trạng thái tách riêng: **nội dung, thanh toán, quyền hiển thị, đơn sản xuất.** |

### Còn mở

| # | Câu hỏi | Ảnh hưởng |
|---|---|---|
| 1 | Mảng 04 (nghĩa trang) nằm trong **cùng một hệ thống** hay là **sản phẩm tách riêng**? | Kiến trúc đa tenant khi làm P2 |
| 2 | Cần **đa ngôn ngữ (Việt/Anh)** ngay không? | Cấu trúc nội dung |
| 3 | Bản nháp chưa thanh toán lưu **bao nhiêu ngày**, tính từ lúc nào, và xử lý ra sao khi hết hạn? | Vòng đời bản nháp (D5.5) |
| 4 | Gói Basic: **dung lượng tối đa mỗi ảnh** và **giới hạn tiểu sử**? Năm ảnh tính cả ảnh chân dung và ảnh bìa nếu là hai tệp khác nhau. | Chống hiểu "5 ảnh" là dung lượng không giới hạn |
| 5 | Giá và trần dung lượng của **các gói nâng cấp** (ảnh, âm thanh, video)? | Bảng giá sau Basic |
| 6 | Bảng **gốm**: mẫu, cách chế tác, điều kiện dùng trong nhà/ngoài trời, sau khi kiểm tra sản phẩm thật? | Có mở bán gốm hay chưa |

---

**Tài liệu liên quan:**
- [01 — Danh mục chức năng Web & App](./01-DANH-MUC-CHUC-NANG.md)
- [02 — Flow chức năng chi tiết](./02-FLOW-CHUC-NANG-CHI-TIET.md)
