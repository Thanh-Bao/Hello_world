### Phần 1: Overview

|                                                                                                                                                      |                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| [bestofjs.org](https://bestofjs.org/projects)                                                                                                        | library trend                    |
| [bestofjs.org/timeline](https://bestofjs.org/timeline)                                                                                               | library timeline                 |
| [stateofjs.com](https://2022.stateofjs.com/en-US/)                                                                                                   | JS servey                        |
| [github.com/anvaka](https://gist.github.com/anvaka/8e8fa57c7ee1350e3491)                                                                             | Top npm download                 |
| [stackoverflow](https://survey.stackoverflow.co/2022/)                                                                                               | stackoverflow survey             |
| [gitstar-ranking.com](https://gitstar-ranking.com/repositories)                                                                                      | github repositories ranking      |
| [itviec.com](https://itviec.com/blog/wp-content/uploads/2022/11/N8VdVWP6dt58ys1b1Zdln2508hnt2cesc5ssv28k6tbyi-ITviec_Salary_Report_2022_2023-EN.pdf) | survey in vietnam                |
| [npmtrends.com](https://npmtrends.com/)                                                                                                              | compare downloads of the library |
| [jetbrains.com](https://www.jetbrains.com/lp/devecosystem-2022/)                                                                                     | survey by jetbranins             |
| [stateofapis.com](https://stateofapis.com/)                                                                                                          | web API survey                   |
| [github.com](https://octoverse.github.com/2022/top-programming-languages)                                                                            | github statistical               |

---

### Phần 2: Chuẩn bị trước khi học react

- Cần phân biệt giao diện **SPA** (Single page application) và **MPA** (multi page application). Phân biệt **CSR** (Client side render) và **SSR** (server side render).
- SEO (search engine optimization).
- Những loại web nào cần SEO, những loại web nào không cần SEO?
- React khi nào cần nodeJS, khi nào không cần dùng nodeJS?
- Phân biệt react với một số framework dựa trên react: [nextJS](https://nextjs.org), [qwik](https://qwik.builder.io/), [solidJS](https://www.solidjs.com/), [Preact](https://preactjs.com/), [fresh](https://fresh.deno.dev/), ...
- Phân biệt router phía client và router phía server.

### Phần 3: React

- Phân biệt được state và props
- Khi nào sử dụng state, khi nào sử dụng props
- Ôn lại phần ES6 module (import & export) và destructuring

| docs                                                                         | description                   |     |
| ---------------------------------------------------------------------------- | ----------------------------- | --- |
| [reactjs.org](https://beta.reactjs.org/)                                     | web                           |
| [expo.dev](https://docs.expo.dev/), [react native](https://reactnative.dev/) | mobile (IOS + Android)        |
| [react + electron](https://www.electronjs.org/)                              | Desktop app (windows + MacOS) |
| [react + babylonJS](https://www.babylonjs.com/)                              | mobile game (unpopular)       |

### Phần 4: React UI kit

|                                                                |                     |
| -------------------------------------------------------------- | ------------------- |
| [sap.github.io](https://sap.github.io/ui5-webcomponents-react) | developed by SAP    |
| [mui.com](https://mui.com/)                                    | design by google    |
| [ant](https://ant.design/)                                     | by alibaba          |
| [fluentUI](https://react.fluentui.dev/)                        | design by Microsoft |

### Phần 5: validation

Tất cả dữ liệu lấy từ user để gửi đến server đều phải được validation trước khi lưu vào database.
Bắt buộc validation ở 2 vị trí:

- Phía server tại controller (nơi tiếp nhận body của http POST, PUT, ...) phải validate data để **bảo vệ server**, và **đảm bảo tính nhất quán** khi lưu vào database.
- Phía frontend: validate để hạn chế user nhập sai format.
  Dữ liệu do server response, frontend không cần validate. Validation khác với verify. Các trường hợp validation thường gặp:
  check format số điện thoại, ô nhập số không được nhập text, check không quá 255 ký tự, check format ngày tháng .... hoặc username đã có người đăng ký, không được đặt lại password đã sử dụng trước đó, thẻ VISA không hợp lệ, .... mọi field input đều phải check `null`, empty text, min value, max value.

|         | implement                                                                                     | use case                                                                                                                                                                                                                                              |
| ------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Level 1 | sử dụng if-else, switch-case, ...                                                             | form đơn giản, ít field                                                                                                                                                                                                                               |
| Level 2 | sử dụng Regex (regex không phụ thuộc ngôn ngữ lập trình)                                      | field có điều kiện phức tạp VD: mật khẩu không được quá 255 ký tự, tối thiểu 8 ký tự, phải bao gồm ít nhất một chữ in hoa, chữ in thường, số và ký tự đặc biệt. Không được chưa các ký tự liên tiếp như 123, ABCD. password không được chứa username. |
| level 3 | sử dụng [yup](https://www.npmjs.com/package/yup)                                              | code ngắn, đồng nhất khi có nhiều form, nhiều điều kiện.                                                                                                                                                                                              |
| level 4 | sử dụng 1 thư viện riêng biệt chuyên xử lý form kết hợp với một thư viện chuyên validate data |

### Phần 6: Thực hành

- Chuyển UI html,CSS ở checkpoint 3 thành project reactJS.
- Config project reactJS đó để build app desktop.
- Tái sử dụng code logic của reactJS để làm app di động.

---

### Best practice

1. Xử lý form:
   1.1. Chọn loại input hợp lý khi cần lấy data từ user. VD:

- Chọn địa chỉ thì phải selection dropdown, mỗi field phải có ô search, tên thành phố phải sắp xếp theo bảng chữ cái.
- Giới tính phải dùng `radio button` (tick box hình tròn).
- Nên kết hợp icon: Chọn quốc gia phải có icon quốc kỳ phía trước, những button nhỏ không đủ width để hiển thị `label`
  phải dùng icon thay thế.
- Khi user click button submit phải css mờ button này và hiển icon loading, đồng thời disable button này để tránh user click lần thứ 2 trong khi request lần 1 chưa xử lý xong (disable button, không phải hiden)
- field không cho phép nhập phải disable (bị mờ)
- Mỗi field phải có ít nhất một trong 3 thẻ đi kèm: icon trước field, label, placeholder.
- Cần phải có example data với những field dễ gây confuse. Example: Nguyen Van An cho ô họ tên, SDT, ....
- User có thể ấn phím `tab` để con trỏ chuột tự di chuyển giữa các field.

2. validation

- Những loại data cần kết nối internet để validate: Số thẻ credit, ID, username, ... cần hiển thị icon tích xanh, hoặc dấu x đỏ sau mỗi field. Dữ liệu thông thường: Firstname, lastname, ... không cần icon.
- Nếu user nhập sai phải hiển thị text màu đỏ bên dưới field thông báo lý do lỗi và hướng dẫn sửa lại đúng.

3. Khi xử lý http luôn phải xử lý UI với 3 trạng thái:

- Connecting.../Processing... : hiển thị animation loading.
- successful
- error: phải hiển thị thông báo lỗi, khi lỗi phải giữ nguyên data mà user đã nhập trên màn hình. **Trừ khi user đóng tab hoặc user chủ động ấn nút clear thì không được tự xóa data user nhập trên frontend**.
