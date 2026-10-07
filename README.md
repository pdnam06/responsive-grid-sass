# Responsive Grid — tái cấu trúc bằng Sass

Nguồn bài thực hành: [codegym-vn/responsive-grid](https://github.com/codegym-vn/responsive-grid), commit `b744bf20dfade2b357abfd53563c273fecb1d128`.

Mã HTML mẫu và lịch sử Git gốc được giữ lại. Bản gốc để đối chiếu nằm trong original/responsive_grid.htm.

## Thay đổi
- Tách CSS trong thẻ style và các thuộc tính style khỏi HTML, thay bằng class.
- Đưa màu sắc, độ rộng cột, chiều cao hàng, khoảng cách và opacity vào biến.
- Mixins full-row, surface-column và blue-panel dùng lại định dạng cho các khối tương tự.
- Nesting áp dụng cho các đường chia cột và trạng thái first-child/last-child.
- Dùng @use và namespace để nạp từng partial.
- Giữ nguyên lưới float 12 cột của mẫu, gồm cột 8.33%, hai vùng rộng 25%, header, footer và các đường lưới nền. Bố cục co giãn theo phần trăm như bản gốc; không thêm breakpoint xếp dọc vì bài yêu cầu tái cấu trúc CSS.
- Bỏ khai báo nền #84c754 vì ngay sau đó đã bị #f1f1f1 ghi đè trong CSS gốc.

## Cấu trúc
```text
scss/
  abstracts/
    _variables.scss
    _mixins.scss
  base/
    _reset.scss
  layout/
    _grid.scss
  components/
    _blocks.scss
    _guides.scss
  main.scss
styles.css
responsive_grid.htm
index.html
original/responsive_grid.htm
package.json
package-lock.json
verification.txt
desktop.png
mobile.png
```

responsive_grid.htm giữ tên tệp theo repository gốc. index.html có cùng nội dung để mở trang mặc định trên GitHub Pages. Trình duyệt chỉ nạp styles.css đã biên dịch.

## Cài đặt và chạy
Trong thư mục dự án:
```powershell
npm.cmd ci
npm.cmd run build
```
Mở index.html hoặc responsive_grid.htm bằng trình duyệt.

Biên dịch trực tiếp khi đã cài Sass toàn cục:
```powershell
sass.cmd scss/main.scss styles.css --no-source-map
```

Tự biên dịch khi sửa SCSS:
```powershell
npm.cmd run watch
```
Sửa biến trong scss/abstracts/_variables.scss, lưu và tải lại trang. Dừng bằng Ctrl+C. Không chỉnh styles.css trực tiếp.

## Kiểm tra
Biên dịch thành công bằng Dart Sass 1.105.1. Đã so sánh vị trí, kích thước và định dạng của tất cả 34 div với bản gốc ở 1440px, 768px, 390px và 320px: khớp, không tràn ngang. HTML mới không còn CSS nội tuyến. Kết quả lưu trong verification.txt, ảnh trong desktop.png và mobile.png.
