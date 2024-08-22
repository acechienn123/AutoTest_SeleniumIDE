Selenium IDE
biểu tượng

Môi trường phát triển tích hợp cho các tập lệnh Selenium Selenium IDE là một ứng dụng điện tử được viết để cho phép ghi và phát lại các tập lệnh Selenium.

Cài đặt
Việc cài đặt có thể được thực hiện theo nhiều cách khác nhau:

Các tệp nhị phân đóng gói sẵn có thể được cài đặt trực tiếp dưới dạng bản phát hành trên github.
Selenium-ide có thể được cài đặt thông qua npm npm install -g selenium-idevà chạy selenium-idetrực tiếp.
Ứng dụng này có thể được xây dựng thủ công bằng cách sử dụng các hướng dẫn bên dưới.
Xây dựng thủ công
Để xây dựng thủ công, bạn phải cài đặt các điều kiện tiên quyết dưới đây và làm theo các bước sau đó.

Điều kiện tiên quyết
Git
NodeJS v16
Pnpm
Xây dựng
git clone https://github.com/SeleniumHQ/selenium-ide- Sao chép kho lưu trữ IDE
cd selenium-ide- Điều hướng vào thư mục IDE
pnpm -r i- Cài đặt các phụ thuộc
pnpm run build- Xây dựng ứng dụng
pnpm run start- Chạy ứng dụng
Bây giờ thì sao?
Sau đây là bản thảo các nhiệm vụ chung sắp tới. Hãy thoải mái tham gia và nêu rõ nhiệm vụ mà bạn muốn đảm nhiệm:

Độ chính xác của bộ chọn - một tùy chọn là xếp hạng bộ chọn - chúng ta có thể tối ưu hóa độ chính xác của bộ chọn và kiểm tra tính ổn định bằng cách thu thập càng nhiều thuộc tính càng tốt cho mỗi sự kiện của người dùng. Các thuộc tính có khả năng xảy ra nhất sẽ được sử dụng cho bộ chọn, với các thuộc tính dự phòng cho các thuộc tính khác.
Chỉnh sửa thông minh
Xuất sang mã selenium bằng nhiều ngôn ngữ khác nhau
Đóng góp
Nếu bạn muốn đóng góp vào cơ sở mã, hãy bắt đầu bằng cách xây dựng thủ công bằng các lệnh trên. Các mẹo dưới đây cũng nhằm hỗ trợ bạn.

Nếu bạn muốn lặp lại nhanh hơn, yarn watchsẽ tạo điều kiện cho việc xây dựng lại gần như theo thời gian thực để lặp lại nhanh chóng (thực hiện thay đổi -> yarn start-> kiểm tra thay đổi)
Để kích hoạt devtools trên một trang CommandOrControl+F12hoặc CommandOrControl+Option+Isẽ mở devtools. Để thuận tiện cho bạn, React Developer Tools được cài đặt sẵn trong môi trường electron.
VSCode có cấu trúc không gian làm việc và lệnh chạy được xác định, cũng như ánh xạ tệp để cho phép các điểm dừng hoạt động trên các bản đồ nguồn cho quy trình chính.
Bạn có thể localhost:8315sử dụng công cụ phát triển Chrome tại đây nếu công cụ phát triển nội tuyến không đủ, mặc dù tôi thực sự khuyên bạn nên sử dụng công cụ phát triển trong cửa sổ vì chúng cũng cài đặt Công cụ phát triển React.
Bạn có thắc mắc hoặc muốn trò chuyện không?
Nếu bạn có thắc mắc, hãy xem phần Câu hỏi thường gặp của chúng tôi .

Bạn cũng có thể tìm thấy chúng tôi trên kênh IRC #selenium, cũng có trên Slack .

Ngành kiến ​​​​trúc
Codebase là javascript và dựa nhiều vào hệ sinh thái NodeJS, Electron và React. Đây là tập hợp các gói được sắp xếp trong cấu hình monorepo. Ngoại trừ các gói code-export không được định kiểu hoàn toàn, các gói này được định kiểu hoàn toàn bằng Typescript.

Gói hàng
Đây là các gói chính. Chúng được sử dụng để chạy chương trình:

selenium-ide: Ứng dụng Electron chính. Được xây dựng bằng webpack, react frontend. Giao tiếp thông qua các giao thức IPC.

side-runner: NodeJS Task Runner. Được xây dựng bằng typescript.

side-cli: Cli thử nghiệm sử dụng react và ink.

side-runtime: Trình bao bọc hệ thống phát lại. Lấy các tệp bên và thực thi chúng. Được sử dụng bởi cả selenium-ide và side-runner.

side-api: Đây là hình dạng api của selenium-ide. Điều này nhằm mục đích giúp chia sẻ các loại api với các plugin theo cách ít tốn dung lượng hơn.

side-model: Được sử dụng để cung cấp siêu dữ liệu xung quanh các lệnh và kiểu đối số chuẩn.

side-commons: Giống như thư mục utils/helpers thông thường, ngoại trừ việc nó được dùng để chia sẻ giữa các gói thay vì chỉ trong các thư mục.

side-code-export: Trình biên dịch NodeJS cho các tệp .side. Được sử dụng để xuất sang các ngôn ngữ khác (csharp, java, javascript, python, ruby).

code-export-*: Định dạng xuất mã cho nhiều ngôn ngữ khác nhau
