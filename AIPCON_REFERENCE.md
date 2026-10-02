# AIPCON · Tài liệu tham chiếu (Web V10 ↔ App V1a)

> File tham chiếu gọn để dùng trong Project. Bản đầy đủ có ảnh: `AIPCON_Design_V10.html` (web) và `AIPCON_APP_DESIGN_V1a.html` (app).
> **File làm việc hiện tại: `AIPCON_APP_DESIGN_V2a.html` — chỉ phát triển nền trắng.** V2 (có nền navy) giữ lại để đối chiếu, không chỉnh tiếp. V2a chỉ gồm màn hình điện thoại, không còn cột điều hướng hay ghi chú thiết kế — mọi thao tác đi như app thật.
> **Quy tắc đã chốt (30/09/2026):** giữ nguyên toàn bộ design của App V1a. Web V10 chỉ dùng để tham chiếu **flow và nội dung**, không dùng để thay đổi giao diện app.

## 1. Sitemap Web V10 (36 màn)

| Nhóm | Màn (id) | Ghi chú |
|---|---|---|
| Khám phá | s-home, s-services, s-results | Trang chủ → Dịch vụ theo hành trình → Danh sách theo loại |
| Chi tiết dịch vụ | s-pdp (Lounge), s-elite, s-elite2, s-elitep (SH Elite / Elite+), s-pdpft (Fast Track), s-pdpfnb (F&B), s-pdpatt (Điểm tham quan), s-pdptrf (Xe đưa đón), s-pdpwel (Lounge Wellness) | Mỗi loại dịch vụ có layout chi tiết riêng |
| Mua | s-cart, s-checkout, s-done | Giỏ → Thông tin & thanh toán → Thành công |
| Đặt lịch | s-booktransfer → s-tfcheckout → s-bookdone (xe) · s-bookelite (Elite+) · s-ftbook (Fast Track) · s-booklookup (đặt lịch bằng mã) · s-bkview | Sau khi mua, voucher cần đặt lịch |
| Gói & quà | s-packages, s-combo (Combo), s-gift, s-giftpick (Gift Pass) | |
| Thành viên | s-acp (giới thiệu thẻ), s-acptier (hạng thẻ), s-account, s-signup | Đăng nhập dạng popup, header 2 trạng thái |
| Doanh nghiệp | s-business | Thẻ doanh nghiệp trả theo lượt · Gift Pass/combo theo yêu cầu · đại lý chiết khấu theo cấp |
| Nội dung | s-news, s-article, s-faq, s-policy, s-contact | |

**Luồng chính trên web:** Home → Services → Results → PDP → (Mua ngay → Checkout | Thêm giỏ → Cart → Checkout) → Done → (Account / Đặt lịch: booktransfer · pdpft/ftbook · bookelite · booklookup).

## 2. Đối chiếu App V2 với Web V10

| Web V10 | App V2 | Trạng thái |
|---|---|---|
| home, services, results, pdp, pdpft, elite, cart, checkout, done, account, acp, acptier | Luồng mua dịch vụ, giỏ hàng, tài khoản, thẻ ACP | ✅ Có từ V1a |
| packages, combo | Gói combo (6 dòng) + chi tiết combo dùng chung màn Chi tiết dịch vụ | ✅ V2 |
| gift, giftpick | Gift Pass, Chọn quà tặng (5 sản phẩm), form người nhận trong Chi tiết | ✅ V2 |
| booktransfer, tfcheckout, bookdone | Đặt xe theo tuyến: giá theo vùng Z1–Z6, 4 loại xe, ngoài vùng → báo giá | ✅ V2 |
| ftbook | Thông tin đặt chỗ Fast Track / Meet & Greet trước thanh toán | ✅ V2 |
| bookelite | Đặt lịch sử dụng voucher (SH Elite+, Wellness, Fast Track) + màn Đã gửi yêu cầu | ✅ V2 |
| booklookup | Đặt lịch bằng mã, không cần đăng nhập, báo rõ lý do mã sai | ✅ V2 |
| news, article | Tin tức & Ưu đãi (6 nhóm) + bài viết | ✅ V2 |
| business | Giải pháp doanh nghiệp, đối tác dạng ô chữ viết tắt | ✅ V2 |
| signup | Đăng nhập / đăng ký / quên mật khẩu, 2 ô đồng ý tách riêng | ✅ V2 |
| faq, contact, policy | Hỏi đáp (5 nhóm, tìm không dấu), Liên hệ, Chính sách (9 văn bản tóm tắt) | ✅ V2 |
| pdpfnb, pdpatt, pdpwel | Chi tiết F&B, Wellness dùng màn Chi tiết chung; Điểm tham quan chưa có | ❓ Cần xác nhận |
| — | Thông tin cá nhân, Đơn hàng & hoá đơn, Dữ liệu cá nhân, Thay đổi/huỷ booking | ⏳ Vòng sau |

## 2b. Nguyên tắc luồng (chốt 30/09/2026)

**Quy tắc nghiệp vụ và thứ tự bước theo web V10 100%. App chỉ khác web ở cách trình bày cho điện thoại.**

Đã chốt giữ nguyên (app khác web, không đổi): thẻ "chuyến bay sắp tới" làm hero trang chủ · tab Đặt lịch ở giữa thanh tab · thẻ ACP nằm trong Tài khoản · trang Thông báo.

Đã chỉnh trong V2 theo web:
- Fast Track / Meet & Greet có 2 cách đặt: "Đặt cho chuyến bay cụ thể" (khai thông tin trước thanh toán → booking, cả khi qua giỏ) hoặc "Mua voucher, đặt lịch sau"
- Xe đưa đón không qua giỏ: màn chi tiết chỉ có "Đặt chuyến" → luồng đặt xe theo tuyến; giá gói ở màn chi tiết = giá vùng Z1
- Voucher đã có booking không đặt lần hai (trạng thái "Đã gửi yêu cầu" / "Đã đặt chỗ")
- Gift Pass: người nhận khai ở bước thanh toán, mỗi thẻ một người nhận; quà đã mua hiện ở Đơn hàng, không vào ví người mua
- Trạng thái chưa đăng nhập: trang chủ, Đặt lịch, Thông báo, Thẻ ACP hiện lời mời đăng nhập; thanh toán để trống thông tin; vẫn mua và đặt lịch bằng mã được
- Khuyến mại hết hạn tự ẩn; booking mới sinh thông báo

Giả định cần bên yêu cầu xác nhận: combo có định danh thu họ tên + số giấy tờ ở bước thanh toán · Gift Pass đã mua hiện ở Đơn hàng.

## 3. Hệ thống UI của App V1a (nguồn chuẩn cho app, giữ nguyên)

- **Chế độ:** từ V2a chỉ còn nền trắng (đã gỡ nút đổi nền và toàn bộ CSS nền navy). Bảng màu dark bên dưới chỉ để tham khảo lịch sử.
- **Font:** display `SVN-Aptima` (fallback Be Vietnam Pro, Georgia) · body `Be Vietnam Pro`. File app **chưa nhúng** SVN-Aptima; web V10 có nhúng.
- **Màu (light / dark):**
  - Chữ `--tx` #232360 / #FFF5E4 · `--tx2` #454973 · `--tx3` #6A6D92
  - Nền `--bg` #FFFFFF / #0C1236 · `--s2` #F4F5F8 / #1B2356 · thẻ `--card` #232360 / #1A2152
  - Gold `--gold` #9C6D2A / #D2AE62 · gradient #B38A45 → #E2C68A
  - Trạng thái: ok #2F6B4F · warn #9C6D2A · err #8C3232 · info #3F4C9A
- **Cần chuẩn hoá (không đổi giao diện, chỉ gom giá trị):** khoảng 20 cỡ chữ lẻ (10.5–30px), khoảng 10 giá trị bo góc, khoảng 9 sắc gold viết cứng ngoài token.

## 4. Quy ước đã chốt trên Web V10 (tham khảo, không bắt buộc cho app)

- Token web: navy #1B1E3D · brand #9C6D2A · cream #F5F0EA · bo góc chuẩn 6px · sans Roboto · serif SVN-Aptima
- Thang chữ mobile web: Display 28/300 serif · Section 24/300 · Tiêu đề thẻ 22/400 (thẻ danh sách 17) · Eyebrow 11/500 IN HOA · Thân 14/1.6 · Phụ 13 · Meta 12.5 · Nút 14/600 (nhỏ 13/600)
- Vùng chạm tối thiểu 44px · một kiểu tab duy nhất (gạch chân vàng khi chọn) · một kiểu link có mũi tên · gạch chân chỉ dùng cho tab/bộ lọc; lựa chọn trong form dùng thẻ radio

## 5. Việc còn mở

- Phạm vi V2: chỉ chuẩn hoá hay làm thêm màn từ danh sách vòng sau
- Web dùng navy #1B1E3D, app dùng #232360: có cần thống nhất không


## 6. Quy ước UI đã chốt trên V2a (nền trắng)

- **Tab vs chip:** tab (chữ + gạch chân vàng, cao 44px) dùng để chuyển nhóm nội dung; chip chỉ dùng cho bộ lọc.
- **Lựa chọn 2 phương án loại trừ** (Cách đặt, Chiều đi, Nhà ga, Định danh): ô chia đôi, không nút tròn, chọn thì viền + chữ vàng đồng.
- **Lựa chọn gói có giá:** ô có nút tròn (radio), viền 1px, không đổi độ đậm chữ khi chọn.
- **Nút chính:** vàng kim chuyển sắc đậm, chữ/icon trắng. Nút phụ: viền vàng đồng. Hành động phụ ở màn hoàn tất: đường dẫn chữ, không viền.
- **Thanh đáy có tổng tiền + 2 nút:** 2 tầng (Tạm tính / số tiền ở trên, 2 nút chia đôi ở dưới).
- **Thanh tab:** 5 tab giống nhau, nền phẳng; đang chọn = icon + chữ vàng đồng, chưa chọn = xám nhạt.
- **Màu:** thẻ ACP là khối đậm duy nhất (kim loại theo hạng); nội dung trang chủ trắng, trạng thái dạng chữ + chấm tròn.
- **Thẻ ACP:** chạm để lật ra QR (làm mới 30 giây, tự lật về sau 60 giây, có Phóng to).
- **Khối Ví (trang chủ, Tài khoản):** danh sách 3 dòng, nút tròn bên phải (QR / Đặt lịch / Xem booking); "Xem tất cả" mở màn Ví của tôi.
- **Câu chữ:** ngắn, không văn nói, mỗi ý một dòng; không có câu sub dưới tiêu đề trừ khi là note.
- **Điều kiện sử dụng:** danh sách chữ có chấm đầu dòng, không đóng khung.

## 7. Hạng mục chưa làm (tính đến 01/10/2026)

**Web có, app chưa có**
- Mua làm quà cho mọi dịch vụ (Cho tôi / Tặng điện tử / Tặng vật lý ngay ở trang chi tiết)
- Gợi ý mua kèm ("Đừng quên Xe Đưa Đón!", ưu đãi Combo Trọn chuyến)
- Phòng chờ quốc tế Plaza Premium; Điểm tham quan (Ba Na Hills); danh sách F&B đầy đủ
- Fast Track chi tiết hơn (gói VIP)
- Lịch sử điểm hạng thẻ ACP
- Thay đổi / huỷ booking thao tác trong app (hiện hướng gọi tổng đài)
- Tải hoá đơn điện tử
- Đa ngôn ngữ (để sau cùng)

**Trạng thái lỗi / trường hợp biên**
- Thanh toán thất bại, hết thời gian, màn cổng thanh toán / VietQR
- Nhập OTP khi đăng nhập / quên mật khẩu
- Voucher hết hạn, dịch vụ hết suất trong giỏ
- Kiểm tra dữ liệu nhập form (bỏ trống, sai định dạng)

**Đề xuất đã đưa, chờ anh/chị quyết**
- Điểm hạng đang hiện ở cả mặt trước thẻ ACP và box điểm bên dưới (trùng thông tin) — cân nhắc giữ một chỗ
- Nhãn "Cần đặt lịch sau khi mua" trên dòng voucher Fast Track (mua voucher trước) ở giỏ hàng và thanh toán
- Bỏ note "Khai chuyến bay… / Xác nhận trong 2 giờ" ở trang chi tiết Fast Track / Meet & Greet
- Rút gọn nội dung FAQ, chính sách, tin tức

**Chờ bên yêu cầu xác nhận**
- Combo có định danh thu họ tên + giấy tờ ở bước thanh toán (giả định)
- Gift Pass đã mua hiện ở Đơn hàng (giả định)
- Giá Combo Elite Experience (đang 950.000đ/lượt theo V1a)
- Nội dung Chính sách Lounge Pass (đã tạm bỏ khỏi app)
- Quyền dùng tên/logo đối tác (đang là ô chữ viết tắt)
- Có làm màn Điểm tham quan không; thông tin gói và giá Xe điện trong nhà ga (đang "Sắp ra mắt")

**Round chuẩn hoá hệ thống UI (chưa làm)**
- Gom cỡ chữ, bo góc, màu lẻ thành token; xuất trang Design System cho dev
- Màu thương hiệu đối tác trong màn Doanh nghiệp đang nằm ngoài guideline

## Changelog
- 01/10/2026 · V2a chỉnh tay bằng code (anh/chị), đã đối chiếu và chạy kiểm tra 38/38 đạt:
  - **Thẻ ACP mới** (trang chủ + trang Thẻ ACP): chất liệu kim loại đổi màu theo hạng (Sky / Sky Plus / Sky Stella / Sky Infinity), viền trong, vân xước, ánh sáng; mặt trước có "Hạng hội viên", tên, số thẻ, điểm, thanh tiến độ mảnh và "Chạm để xuất trình"
  - **Chạm thẻ = lật thẻ**: mặt sau hiện QR, mã tự làm mới mỗi 30 giây (vòng đếm ngược), tự lật về sau 60 giây; nút "Phóng to" mở QR lớn dạng popup giữa màn hình; hỗ trợ phím Enter/Space
  - **Khối Ví ở trang chủ**: đổi từ băng thẻ trượt ngang sang danh sách 3 dòng (ảnh nhỏ, tên, trạng thái · mã, nút QR tròn bên phải), giống khối Ví ở Tài khoản; vẫn giữ tab Sẵn sàng / Chờ lịch
  - **Tab Đặt lịch**: ô "Đặt lịch bằng mã voucher" (mã + email + nút "Kiểm tra mã & đặt lịch") đặt ngay đầu tab, kết quả hiện ngay bên dưới không chuyển trang (có "Nhập mã khác"); thêm "Không có mã trong tay?" → Chọn từ Ví / Gọi tổng đài; bỏ nút "Đặt lịch bằng mã voucher" cũ; nút "Đặt lịch" trong danh sách chờ đổi sang nút phụ; tiêu đề nhóm dùng kiểu phụ (.sec.sub)
  - **Đặt lịch khi chưa đăng nhập**: cũng hiện ô nhập mã ở đầu, phần Booking của tôi là lời mời đăng nhập
  - Ghi chú kỹ thuật: CSS còn vài class chưa dùng (.map, .emv, .lkrow) — có thể dọn ở round chuẩn hoá
- 30/09–01/10/2026 · V2a (vòng chỉnh UI):
  - Tab Dịch vụ: bỏ mô tả và giá dưới tên; icon (i) cạnh tên để xem chi tiết; nút "Chọn" mở bảng mua nhanh (chọn dịch vụ/gói/số khách, Thêm vào giỏ / Mua ngay); Xe đưa đón = "Đặt xe" mở bảng đặt xe nhanh (tuyến hay đặt + ô nhập địa chỉ + chọn xe); Doanh nghiệp = "Liên hệ"; "Phòng khách thương gia" → "Phòng chờ thương gia"; Xe điện trong nhà ga → "Sắp ra mắt"
  - Fast Track / Meet & Greet: "Đặt cho chuyến bay" → 2 nút "Nhập thông tin / Mua ngay" đều tới màn Thông tin đặt chỗ (có thẻ tóm tắt dịch vụ + nút Đổi, đáy có Thêm vào giỏ / Mua ngay); "Mua voucher trước" → Thêm vào giỏ / Mua ngay như thường
  - Gói combo & Gift Pass: thẻ chọn nhanh (chọn số lượt / Thẻ vật lý – Thẻ điện tử + Mua ngay ngay trên danh sách); Gift Pass khai người nhận ở thanh toán
  - Trang chủ: bỏ thanh tìm kiếm và nút chọn sân bay, thay bằng nút tìm kiếm toàn app; box điểm "340 / 600 điểm · Còn 260 điểm lên Sky Stella"; khối Ví của tôi; thẻ Chuyến bay sắp tới nền trắng (thẻ ACP và khối Ví được chỉnh tiếp ở dòng dưới)
  - Tài khoản: khối Ví của tôi (3 voucher, nút QR tròn); Thẻ ACP & hạng thẻ tách khỏi Ví
  - Màn mới: Ví của tôi (Tất cả / Sẵn sàng / Chờ lịch / Đã dùng), Tìm kiếm toàn app (dịch vụ, voucher theo mã, booking, tin tức, FAQ, chính sách, lối tắt)
  - Màn hoàn tất: hành động chính là nút trong thẻ, hành động phụ là đường dẫn chữ
  - Form: Họ tên 1 hàng, Quốc tịch + Số hộ chiếu/CCCD 1 hàng; email hàng riêng; không ô nào bị cắt chữ
  - Kiểm thử: bộ kiểm tra luồng tự động 38/38 mục đạt
- 30/09/2026 · V2a: bỏ cột điều hướng và toàn bộ ghi chú thiết kế; thay các toast/màn "làm ở vòng sau" bằng hành vi thật — lọc nhà ga và sắp xếp ở danh sách, ô mã giảm giá, form hoá đơn công ty, màn Thông tin cá nhân, Dữ liệu cá nhân của tôi, thân bài tin tức, văn bản Điều kiện sử dụng; chỉ Nội Bài mở bán (sân bay khác hiện "sắp mở bán"); bỏ văn bản Lounge Pass (chưa có nội dung từ web).
- 30/09/2026 · Tạo V2a từ V2: chỉ giữ nền trắng, gỡ nút đổi nền và CSS nền navy; giao diện nền trắng giữ nguyên. Từ đây chỉnh trên V2a.
- 30/09/2026 · App V2 (cập nhật): chỉnh luồng theo web — Fast Track 2 cách đặt, xe không qua giỏ, Gift Pass khai người nhận ở thanh toán + màn Đơn hàng, trạng thái chưa đăng nhập, sửa dữ liệu voucher trùng booking, ẩn khuyến mại hết hạn.
- 30/09/2026 · App V2: dựng 11 hạng mục "vòng sau" của V1a, bổ sung 12 ảnh từ web V10, giữ nguyên design V1a.
- 30/09/2026 · Tạo file tham chiếu từ Web V10 + App V1a.
