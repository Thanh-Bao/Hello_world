## Phân biệt NodeJS và ExpressJS

### Node

- Muốn chơi game trên windows cần phải có Microsoft Visual C++ Runtime.
- Java muốn chạy trên máy chủ thì phải cần có JRE (**J**ava **R**untime **E**nvironment).
- Muốn run code Python cũng cần cài environment.
- Javascript thực thi được trên chrome là nhờ có runtime của chrome execute (V8 engine).

=> NodeJS là runtime enviroment giúp execute JS phía server (Ngoài ra nodeJS cũng đóng vai trò làm enviroment ở giai đoạn build-time trường hợp làm web SPA (react thuần), app di động (react native)) -> NodeJS không phải library, không phải framework, càng không phải tên của một ngôn ngữ lập trình vì nó được tạo ra từ JS.

### ExpressJS

Có nhiều web framework JS dựa trên NodeJS, trong đó ExpressJS là framework được sử dụng nhiều nhất.



## Tổ chức code, chia package, tạo folder

Code backend (Tầng application) thường có 3 phần chính.

- Thư mục Controller/Dispatcher/gateway hay Router ...: Code chuyên xử lý http, URL, nơi tiếp giáp với frontend ("layer đầu của backend")
- Thư mục core với các tên gọi như: Bussiness layer, domain layer, service, ....: VD: Web AI-> phần code AI sẽ code ở đây. Web cho vay-> code tính lãi ở đây. Web quản lý trường học -> viết code sắp xếp thời khóa biểu ở đây. Web mã hóa file -> code xử lý nghiệp vụ sẽ viết tại đây.
- Module kết nối với database thường được đặt tên: Repository, Provider, DataAdapter, DataContext, ... -> code execute SQL viết tại đây. ("Layer cuối của backend")

## Best practice

- ExpressJS và database nên cài đặt trên cùng một máy tính.
- VD Tránh trường hợp database thuê server ở Mỹ, server run expressJS đặt tại Japan.
- Hạn chế sử dụng các API lấy danh sách quốc gia, list city, list district, ... Mở kết nối đến một máy chủ khác làm tăng độ trễ của web, những data này ít biến động, không nhiều nên có thể tự lưu vào server của mình. Trừ trường hợp API ngân hàng, cty giao hàng, API thời tiết, giá cả thị trường, ... bắt buộc phải sử dụng API third-party.

