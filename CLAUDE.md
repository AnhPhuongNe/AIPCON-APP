# AIPCON · Airport Connects App — hướng dẫn làm việc

## File làm việc
- **File chính: `AIPCON_APP_DESIGN_V3.html`** (prototype app di động, 1 file HTML, ~2,6MB, có font/ảnh nhúng base64).
- `index.html` chuyển hướng tới V3; khi lên V4 thì đổi tên file ở cả 2 chỗ trong `index.html`.
- Tài liệu tham chiếu: `AIPCON_REFERENCE.md` (sitemap, quy tắc luồng, quy ước UI, việc còn mở, changelog). Đọc file này trước khi chỉnh luồng hoặc thêm màn.
- Chỉ để đối chiếu, **không chỉnh**: `AIPCON_Design_V10.html` (web, nguồn flow và nội dung), `AIPCON_APP_DESIGN_V1a.html` (nguồn design gốc), `AIPCON_APP_DESIGN_V2a*.html` (bản trước), `MOCKUP_THE_ACP*.html` (mockup thẻ ACP).
- Bản nháp đang chờ duyệt: `_preview/V3_tinhgian.html`, dựng bằng `sh _preview/build.sh` từ `_preview/V3_src.html` (bản sao V3, sửa HTML/JS ở đây) + `_preview/tinhgian.css` + `_preview/tinhgian.js`. Khi duyệt: `cp _preview/V3_tinhgian.html AIPCON_APP_DESIGN_V3.html`, rồi chép V3 mới sang `V3_src.html` và làm rỗng 2 file css/js trước khi nháp vòng sau. Thư mục `_preview/` bị `.gitignore`.
- **Ô lựa chọn (chốt 02/10/2026, phương án A):** thanh trượt không viền, một khối nền be ấm rất nhạt (token `--trk` = gold-600 7% trên trắng), mục đang chọn nổi nền trắng. Nút cộng trừ dùng cùng `--trk`. Vùng mua ở trang chi tiết nền trắng. Danh sách lựa chọn (chọn xe, quà, liệu trình…) và chip theo một quy tắc: **ô trắng nổi = bấm được · viền "đang chọn" = token `--sel-stroke` (2px vàng đồng #9C6D2A) cách mép `--sel-offset` 2px, giữ viền xám mảnh bên trong, nền trắng — giống ô nhập khi focus · nền xám phẳng, chữ xám = không chọn được**. Mọi trạng thái chọn/focus có viền đều dùng 2 token này (ô nhập focus, mục danh sách, chip); ô lỗi dùng cùng độ dày, màu đỏ. Không dùng chấm tròn radio. Chip xuống dòng, không trượt ngang.
- **Icon trong nội dung** (danh sách, lưới, thông báo): nét mảnh, không ô nền, màu xám `--tx3`; ô không chọn được dùng `--ink-400`. Màu vàng chỉ cho hành động chính và trạng thái đang chọn.
- **Đồng bộ booking & voucher ở mọi trang** (Trang chủ, Thông báo, Đặt lịch, Dịch vụ, Ví): trạng thái lấy duy nhất từ `BOOKINGS[].stt`, luôn hiện bằng nhãn `.st`; voucher đã đặt chỗ hiện nhãn của booking. Ngày trong dòng dạng "T7, 05/09" (`bkDate`). Dòng booking: tên dịch vụ / ngày · nơi dùng (`bkSub`). Dòng voucher: tên dịch vụ / nơi dùng · mã (`wName`).
- **Luồng mua:** popup (bảng mua nhanh) chỉ mở từ trang Dịch vụ (mua ngay, không đọc chi tiết). Từ trang chi tiết, nút mua chuyển thẳng sang bước tiếp (Thanh toán, Thông tin đặt chỗ, màn Đặt xe), không mở popup.
- **Vùng mua ở trang chi tiết phải có đủ mọi lựa chọn và thông tin cần nhập như popup Mua ngay** (người dùng có thể vào chi tiết khi chưa chọn gì), và ngược lại popup không được thiếu thông tin thu thập so với trang chi tiết. Cùng nhãn, cùng giá trị mặc định, cùng lưu vào `S.f`; Tạm tính hai nơi phải bằng nhau và bằng Thanh toán. Xe đưa đón dùng chung `tfSheet(inPdp)`.
- **Chọn gói / lựa chọn (trang chi tiết + bảng mua nhanh, dùng chung `optPick`):** tối đa 4 lựa chọn dàn ngang (thanh trượt), không ghi giá trên nút (giá nhảy ở Tạm tính); mô tả gói đang chọn hiện dưới hàng nút; chỉ 1 gói thì không hiện. Nền kem + ô trắng nổi chỉ dùng cho chọn ngang; khi phải xếp dọc thì dùng kiểu danh sách (ô trắng, viền `--sel-stroke` khi chọn). Chọn ngang không đổi độ đậm chữ khi chọn (tránh nút đổi độ rộng làm nhóm nhảy); quyết định ngang/dọc ghi nhớ theo bộ lựa chọn + độ rộng khung. Không ghi chú giá dưới hàng nút (vd. "340.000đ mỗi lượt"). Nhãn lặp tiền tố thì rút gọn ("Voucher 200.000đ" → "200.000đ").
- **Trang chi tiết:** vùng thông tin (nền trơn, các phần tách bằng line xám mảnh, "Dịch vụ gồm" 1 cột) tách biệt với vùng mua "Chọn dịch vụ" (giữ nền riêng như V3, tràn hết chiều ngang). Không tự thêm icon, hỏi trước.
- **Mọi vùng cuộn (màn chính, popup) ẩn thanh cuộn** để độ rộng khung không đổi khi nội dung dài/ngắn.
- **Không rớt chữ** trên mọi nút, chip, tab, ô lựa chọn: chữ một dòng; quá dài thì thu một bậc, vẫn không vừa thì xếp mỗi phương án một hàng.
- `_preview/`: server xem trước (`serve.ps1`, cổng 5173, cấu hình trong `.claude/launch.json` tên `preview`) và bản nháp (`V3_draft.html`, `patch.css`).

## Quy tắc đã chốt
- **V3 là bản chốt** (02/10/2026). V1a chỉ còn là lịch sử, không còn là nguồn design. Web V10 chỉ dùng để tham chiếu **flow và nội dung**, không lấy giao diện web áp vào app.
- Hướng design (02/10/2026): **tinh giản mạnh, nhiều khoảng thở**, vẫn rõ ràng trực quan; giữ nguyên nội dung và flow. **Quy ước màu và nút bấm của V3 giữ nguyên** (nút chính chuyển sắc vàng, nút phụ viền vàng, nút "Chọn"/"Đặt lịch" trên dòng, nút QR tròn, số đếm trên tab, nhãn trạng thái có nền, ô tìm kiếm, avatar). Tinh giản chỉ áp vào khoảng thở, khung, icon trong danh sách, tiêu đề nhóm.
- Nghiệp vụ và thứ tự bước theo web V10; app chỉ khác ở cách trình bày cho điện thoại (chi tiết ở mục 2b của `AIPCON_REFERENCE.md`).
- Chỉ phát triển nền sáng. Không thêm lại chế độ nền navy (còn sót vài selector `data-theme="dark"` trong CSS, không cần dùng).
- Chỉ màn hình điện thoại, không cột điều hướng, không ghi chú thiết kế trong file; mọi thao tác chạy như app thật.
- Câu chữ: tiếng Việt, ngắn, không văn nói, mỗi ý một dòng; không thêm câu phụ dưới tiêu đề trừ khi là ghi chú.
- **Không dùng dấu "—"** trong nội dung hiển thị: tên và dòng phụ dùng " · ", câu văn dùng ":" hoặc "," hoặc tách câu, ô trống thì bỏ trống hoặc ghi bằng chữ. Dấu "–" chỉ dùng cho khoảng (06:00 – 22:00).
- Tiêu đề dòng (voucher, thông báo) giữ 1 dòng: chỉ tên dịch vụ; nơi dùng, mã, trạng thái xuống dòng phụ; không lặp thông tin màn hình đã thể hiện (vd. trạng thái trùng tab). Mã voucher luôn hiện đủ.
- Dự án này là app của khách hàng (Airport Connects), dùng bộ nhận diện AIPCON bên dưới, không dùng màu/font iHouzz.

## Độ chính xác nội dung (chốt 02/10/2026)
- Phải đúng theo Web V10 / bên yêu cầu: **giá và danh mục dịch vụ, thông tin cần thu thập (trường form), luồng thao tác, chính sách**.
- Dữ liệu minh hoạ (ngày, tên khách, mã đơn, mốc thời gian, booking mẫu) chỉ là demo, không cần chính xác, không cần hỏi lại.

## Hệ thống thiết kế V3 (nguồn duy nhất: khối `V3 · DESIGN TOKENS` đầu file)
- **Nền màn hình** `--bg` #F9F7F0 (kem) · khung nội dung, ô nhập, popup, nút phụ: trắng #FFFFFF.
- **Chữ** navy #232360 · phụ #454973 · nhạt #6A6D92.
- **Nhấn** vàng đồng `--gold-600` #9C6D2A; nút chính dùng `--grad-btn` (#D2AE62 → #B8904A → #9C6D2A), chữ trắng.
- **Trạng thái** ok #2F6B4F · cảnh báo #9C6D2A · lỗi #8C3232 · thông tin #3F4C9A.
- **Font** tiêu đề `SVN-Aptima` (đã nhúng trong V3) · thân `Be Vietnam Pro`.
- **Cỡ chữ** `--fs-2xs` 11 · `xs` 12.5 · `sm` 13 · `md` 14 · `lg` 15 · `xl` 17 · `2xl` 19 · `3xl` 22 · `4xl` 26 · `5xl` 30 (riêng thẻ ACP: 8.5 / 9.5 / 10).
- **Bo góc** `--r-xs` 4 · `sm` 9 · `md` 13 · `lg` 18 · `pill` 999.
- **Đổ bóng thống nhất** cho khung nội dung và thẻ ACP: `0 1px 2px` navy 5%.
- **Vùng chạm** tối thiểu 44px.
- Luôn dùng token có sẵn thay vì viết cứng giá trị mới. Nếu cần giá trị mới, thêm vào khối token rồi mới dùng.
- File V3 có nhắc tới `AIPCON_DESIGN_SYSTEM_V3.html` nhưng file này **chưa có** trong thư mục.

## Cách làm việc với file
- File lớn có base64: dùng grep/tìm theo tên class hoặc hàm (`vHome`, `walletHome`…), không đọc hay in toàn bộ file, không dán base64 vào chat.
- CSS chỉnh thêm ở V3 được gom thành các khối có chú thích tiếng Việt `/* ... */` gần cuối phần `<style>`; giữ cách viết này.
- Chỉnh xong: mở xem trước (`preview`, http://localhost:5173/AIPCON_APP_DESIGN_V3.html), kiểm tra lỗi console, chụp ảnh cho người dùng xem.
- Lưu phiên bản bằng **git commit** (tiêu đề dạng `V3: <mô tả ngắn không dấu>`), không tạo thêm file `.backup` / `.before-*`.
- Mỗi đợt chỉnh có ý nghĩa: thêm một dòng vào Changelog của `AIPCON_REFERENCE.md`.
- Màn hoặc tính năng mới: làm bản nháp cho người dùng duyệt trước khi đưa vào file chính.
