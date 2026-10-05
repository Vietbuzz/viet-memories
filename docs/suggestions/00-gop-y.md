> Đã nhập vào `docs/overview/` phiên bản 0.2 (05/10/2026). File này giữ làm nguồn quyết định. Chỗ lệch với `01-bo-sung.md` đã xử lý theo file bổ sung: bảng QR là tùy chọn, có thêm gốm khi đã kiểm tra mẫu.

Bạn sửa trực tiếp file **`01-DANH-MUC-CHUC-NANG.md`** theo danh sách dưới đây. Tôi tách rõ phần sửa nội dung cũ và phần bổ sung.

**1. Sửa các mục chưa đúng quyết định đã chốt**

| Mục | Nội dung thay thế / điều chỉnh |
|---|---|
| **A1.3 — Bảng gói dịch vụ** | Tính phí theo **từng hồ sơ người đã khuất**. Thanh toán một lần, lưu trữ trọn đời theo phạm vi gói đã công bố. Một tài khoản quản lý được nhiều hồ sơ. Ghi rõ dung lượng, sản phẩm QR đi kèm, giao hàng và dịch vụ bổ sung |
| **B2.5 — Dung lượng & thời hạn dịch vụ** | Đổi thành **“Gói hồ sơ & dung lượng”**: hiển thị gói đã mua, trạng thái thanh toán, dung lượng sử dụng và quyền lợi. Không hiển thị ngày hết hạn cho hồ sơ đã mua |
| **D5.5 — Quản lý thời hạn & nhắc gia hạn** | Đổi thành **“Quản lý vòng đời bản nháp”**: thời hạn dùng thử, nhắc trước hạn, xử lý bản nháp chưa thanh toán. Không áp dụng gia hạn định kỳ cho hồ sơ đã mua |
| **D2.2 — Loại vật liệu** | Chỉ gồm **mica dùng trong nhà** và **kim loại cao cấp dùng trong nhà/ngoài trời theo thông số sản phẩm**. Kim loại có lựa chọn màu vàng, bạc, đồng, trắng sáng. Bỏ sản phẩm công ty khắc trực tiếp lên đá |
| **D2.3 — Trạng thái sản xuất** | Đổi thành: **Chờ duyệt mẫu → Đang sản xuất → Kiểm tra QR → Đóng gói → Vận chuyển → Đã giao**. Công ty giao bảng khoan sẵn và phụ kiện phù hợp; khách tự lắp |
| **D3.3–D3.4 — Hoa hồng đối tác** | Với đối tác bia mộ: công ty thu phí nền tảng và cấp QR; đối tác tự báo giá, thu tiền khắc đá. Không mặc định công ty trả thêm hoa hồng. Chính sách hoa hồng khác chỉ áp dụng khi có thỏa thuận riêng |
| **C2.4 — Xuất bản hồ sơ** | Bổ sung điều kiện: **đã xác nhận thanh toán, nội dung được chủ hồ sơ duyệt và quyền hiển thị được xác nhận**. Hồ sơ trả phí có thể giữ riêng tư |
| **C2.5 — Gỡ xuất bản / ẩn tạm** | Chuyển từ **P1 lên P0**. Tạm ẩn không làm mất dữ liệu hoặc quyền lưu trữ đã mua |

**2. Bổ sung nhóm chức năng tạo hồ sơ đơn giản — P0**

Thêm vào **C1**:

- **Tạo nhanh:** nhập thông tin cơ bản → tải ảnh và câu chuyện → xem trước.
- **Tự trình bày theo mẫu:** tự bố trí ảnh, tiểu sử, dấu mốc và album; ẩn các mục trống; hiển thị đẹp trên máy tính và điện thoại.
- **Chỉnh sửa nâng cao:** giữ bảy nhóm nội dung hiện có, nhưng không bắt khách hoàn thành cả bảy nhóm mới được xem bản mẫu.
- **Thời hạn bản nháp:** ghi rõ số ngày lưu, thời điểm bắt đầu tính, nhắc trước hạn và cách xử lý khi hết hạn. Mục này hiện chưa có con số được ghi rõ trong tài liệu.
- **Sau thanh toán:** chuyển bản nháp thành hồ sơ được lưu trữ theo gói; giữ nguyên nội dung khách đã nhập.

**Tự trình bày theo mẫu là P0; AI viết tiểu sử vẫn có thể để P1.**

**3. Bổ sung nhóm “Mua gói, thanh toán & giao hàng” — P0**

| Chức năng | Nội dung |
|---|---|
| Chọn gói cho hồ sơ | Nền tảng + bảng mica; nền tảng + bảng kim loại; hoặc nền tảng + QR số qua đối tác bia mộ |
| Tùy chọn bảng | Vật liệu, màu, kích thước, nội dung trên bảng, phụ kiện |
| Duyệt mẫu bảng | Khách xác nhận tên, ngày tháng, bố cục trước khi sản xuất |
| Thanh toán | Tạo đơn, xác nhận tiền, trạng thái chờ/lỗi/thành công; tránh tạo đơn hoặc sản xuất trùng |
| Địa chỉ nhận hàng | Người nhận, số điện thoại, địa chỉ, phí giao, thời gian dự kiến |
| Theo dõi đơn | Khách xem tiến độ sản xuất và vận chuyển |
| Hỗ trợ sau giao | Báo giao hỏng, sai nội dung, QR khó quét; yêu cầu xử lý hoặc làm lại theo chính sách |

Tách riêng **trạng thái nội dung, thanh toán, quyền hiển thị và đơn sản xuất**. Không gom tất cả thành một trạng thái hồ sơ.

**4. Bổ sung nhóm “Dịch vụ biên tập ký ức”**

Đưa vào danh mục phát triển **P1**; giai đoạn đầu có thể vận hành thủ công:

- Đặt dịch vụ viết tiểu sử, phục hồi ảnh, biên tập video cuộc đời.
- Gửi tư liệu và yêu cầu; nhận báo giá.
- Duyệt kịch bản, xem bản dựng, yêu cầu sửa, duyệt bản cuối.
- Theo dõi tiến độ, số vòng sửa và bàn giao.
- Lưu video vào hồ sơ, cho phép khách tải bản cuối.
- Xin phép riêng nếu đăng YouTube hoặc sử dụng để quảng bá.
- Lưu phạm vi đồng ý, phiên bản nội dung được duyệt và yêu cầu gỡ.
- Giữ bản video độc lập với YouTube; QR luôn trỏ về hồ sơ trên nền tảng.

**5. Làm rõ gia phả, quyền riêng tư và kế thừa**

- **B5:** thêm người thân vào cây không tự phát sinh phí. Phân biệt **thành viên gia phả tối giản** với **hồ sơ tưởng niệm trả phí**.
- **A3.2:** dữ liệu người còn sống không mặc định công khai.
- **B4.4:** bổ sung người quản lý dự phòng và quy trình tiếp quản; cho phép xử lý thủ công có xác minh trong MVP.
- **C — Riêng tư:** thống nhất mặc định riêng tư; người quản lý chủ động chọn phần công khai.
- **C — Bảo mật:** kiểm tra quyền ở máy chủ và đường dẫn ảnh/video/tài liệu, không chỉ ẩn trên giao diện.
- **D5:** bổ sung tiếp nhận yêu cầu xóa dữ liệu ngay từ MVP; quy trình tự động có thể làm sau.
- **D2.1:** mã QR giữ nguyên khi chỉnh sửa hoặc chuyển quản lý; không tái sử dụng mã hồ sơ đã xóa cho người khác.

**6. Đồng bộ lại mức ưu tiên**

Đề xuất sửa phần tổng hợp MVP để khớp từng dòng:

| Chức năng | Mức ưu tiên đề xuất |
|---|---|
| Tạo nhanh, mẫu trình bày tự động, bản nháp, thanh toán, giao hàng | **P0** |
| Tạm ẩn hồ sơ | **P0** |
| A2.10 — Đề nghị kết nối | **P1**, bỏ khỏi danh sách MVP |
| B3.3 — Ghi âm trực tiếp | **P1**, bỏ khỏi danh sách MVP |
| C1.7 — AI viết tiểu sử | **P1** |
| C1.8 — AI suy xuất dấu mốc từ tư liệu | **P2** |
| D3.5 — Cổng đối tác | **P2** |
| Video cuộc đời dạng dịch vụ | **P1**; có thể nhận và xử lý thủ công trước |
| Phần mềm nghĩa trang, app native | **P2** |

Tránh ghi phạm vi kiểu **“A2.1–A2.11”** nếu trong đó có mục P1; hãy liệt kê đúng các mã được làm.

**7. Sửa đồng thời file `02-FLOW-CHUC-NANG-CHI-TIET.md`**

Để hai tài liệu không mâu thuẫn, cần cập nhật:

- **F4:** bổ sung tạo nhanh, tự trình bày và vòng đời bản nháp.
- **F7:** bổ sung điều kiện thanh toán trước kích hoạt hồ sơ chính thức.
- **F10:** bỏ luồng gia hạn và ẩn hồ sơ đã mua vì quá hạn; giữ xuất dữ liệu, tạm ẩn và rời dịch vụ.
- **F11–F13:** thêm hành trình khách tự tạo–xem trước–thanh toán; quy trình nhân sự biên tập chỉ dành cho khách thuê dịch vụ.
- **F14:** bỏ công ty khắc đá, lắp đặt và nghiệm thu tại hiện trường.
- **F15:** sửa mô hình đối tác bia mộ theo cách phân chia doanh thu đã chốt.
- **Phụ lục trạng thái/màn hình:** bổ sung thanh toán, chọn bảng, địa chỉ nhận hàng và theo dõi đơn; bỏ trạng thái hết hạn của hồ sơ đã thanh toán.