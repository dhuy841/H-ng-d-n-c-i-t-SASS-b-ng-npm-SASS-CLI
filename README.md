# Hướng dẫn cài đặt Sass bằng npm và Sass CLI

Dự án này minh họa biên dịch SCSS sang CSS bằng Sass CLI. Node.js và npm cần có sẵn trước khi bắt đầu.

## 1. Kiểm tra Node.js và npm

Mở Terminal, PowerShell hoặc Command Prompt:

```text
node -v
npm -v
```

Nếu chưa có, cài Node.js từ [nodejs.org](https://nodejs.org/en/download/); npm được cài kèm.

## 2. Cài đặt Sass

Để dùng Sass trong dự án này, mở terminal tại thư mục dự án và chạy:

```text
npm install
```

Để cài Sass CLI dùng toàn cục trên máy:

```text
npm install --global sass
sass --version
```

Có thể tải bản Dart Sass độc lập từ [GitHub Releases](https://github.com/sass/dart-sass/releases) nếu không muốn cài qua npm.

## 3. Biên dịch một tệp

```text
node ./node_modules/sass/sass.js scss/main.scss css/main.css
```

Lệnh tạo `css/main.css` từ `scss/main.scss`. Các tệp bắt đầu bằng dấu gạch dưới, như `_variables.scss`, là partial để tái sử dụng và không được biên dịch thành CSS riêng.

## 4. Theo dõi thay đổi (watch)

```text
node ./node_modules/sass/sass.js --watch scss/main.scss:css/main.css
```

Giữ terminal chạy trong lúc sửa SCSS. Nhấn `Ctrl+C` để dừng.

## 5. Biên dịch và theo dõi cả thư mục

```text
npm run build
npm run watch
```

Các lệnh tương đương với `sass scss:css` và `sass --watch scss:css`. Mỗi tệp SCSS không phải partial sẽ được biên dịch sang tệp CSS cùng tên trong `css/`, bao gồm các thư mục con. Ví dụ:

- `scss/main.scss` → `css/main.css`
- `scss/components/buttons.scss` → `css/components/buttons.css`

## 6. Xem kết quả

Mở `index.html` trong trình duyệt. Các stylesheet đã biên dịch trong `css/` được liên kết sẵn.

## Lưu ý trên Windows

Không cần đặt `Set-ExecutionPolicy Unrestricted` để dùng Sass; thiết lập này làm giảm an toàn khi chạy script. Nếu PowerShell chặn shim `.ps1`, hãy gọi lệnh Windows tương ứng, ví dụ `npm.cmd install` hoặc `npx.cmd sass --version`, hoặc dùng Command Prompt.
