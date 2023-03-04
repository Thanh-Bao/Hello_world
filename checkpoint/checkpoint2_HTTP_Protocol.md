> Chuẩn bị:
>
> - Giao thức http là gì?
> - Các method http? (POST-PUT-GET-DELETE)
> - Thành phần của một request http?
> - Sử dụng một ngôn ngữ bất kỳ để tạo một request http đến một server bất kỳ.
> - Video tóm tắt: https://m.youtube.com/watch?v=2JYT5f2isg4

---

> Mục tiêu:
>
> - Hiểu được Web API (REST)

---

Hướng dẫn sử dụng:

- https://thongtindoanhnghiep.co/rest-api
- https://www.vietqr.io/en/intro
- Cài một extension JSON format bất kỳ cho browser đang sử dụng (optional)
- Code mẫu tạo http request để lấy data từ sàn HOSE

```javascript
//asynchronous
const getStocks = async () => {
  const HOSEresponse = await fetch(
    `https://finfo-api.vndirect.com.vn/v4/stock_prices?sort=date%3Adesc&q=floor%3AHOSE%2CHNX~type%3ASTOCK&fields=code%2Cdate%2Copen%2Chigh%2Clow%2Cclose%2CnmVolume%2Cchange%2CpctChange&size=100&page=1`
  );
  const stocks = await HOSEresponse.json();
  console.log(stocks);
};

getStocks();
```

# Phần 1: HTTP GET (chữ R trong combo CRUD - Create/Read/Update/Delete)

**Câu 1:**
Cho API Endpoint: https://thongtindoanhnghiep.co/api/city

Lấy danh sách các tỉnh thành ở Việt Nam và sắp xếp mảng theo thứ tự tăng dần của tên tỉnh.
VD: Tỉnh An Giang là phần tử đầu tiên của mảng.

**Câu 2:**

Cho API Endpoint: https://thongtindoanhnghiep.co/api/city/4/district
(Số 4 là mã số của TP.HCM lấy từ câu 1)

Lấy danh sách các quận ở Hà Nôi và sắp xếp mảng tăng dần theo tên quận.

**Câu 3:**

Dựa vào hướng dẫn của thongtindoanhnghiep.co lấy danh sách các phường ở quận Hoàng Mai và sắp xếp mảng
tăng dần theo thứ tự tên phường.

VD: danh sách phường ở Ba Đình https://thongtindoanhnghiep.co/api/district/73/ward

**Câu 4:**

Cho Endpoint https://api.vietqr.io/v2/banks

Tìm swift code (Business Identifier Codes) và logo của ngân hàng Standard Chartered

**Câu 5:**

Requirement: Tìm thông tin công ty khi biết mã số thuế!

- Vào trang chủ của một cty bất kỳ: VD https://www.toyota.com.vn -> Kéo xuống phần footer (dưới
  cùng của trang web) tìm đến Mã số thuế (MST), mã số thuế cũng là mã số giấy chứng nhận đăng ký doanh nghiệp (GCNĐKDN).
  VD: mã số thuế của toyota Việt Nam: 2500150335
- Hoặc search google với từ khóa: "Mã số thuế của Porsche"
- Kết nối đến Endpoint: https://api.vietqr.io/v2/business/0317431816

---

===> Kết hợp với API https://thongtindoanhnghiep.co/api/company/0309546820
(giả sử thongtindoanhnghiep.co bị thiếu field `DiaChiCongTy` 😅 😂 🤣 )
Hãy tìm thông tin chi nhánh BMW Việt Nam.

_Client (frontend) expect:_

```javasctipt

  {
    tenQuocTe: "Bmv Viet Nam Import Export Joint Stock Company",
    DiaChi: "Số 2 ngõ 158 đường Yên Hòa, Phường Yên Hoà, Quận Cầu Giấy, Thành phố Hà Nội, Việt Nam", //lấy từ https://api.vietqr.io/v2/business/0317431816
    ChuSoHuu: "Nguyễn Quang Tuấn"
  }
```

# Phần 2: HTTP POST (chữ C trong CRUD - Create/Read/Update/Delete)

**Câu 6:**

Cho discord endpoint (Web hook): https://discord.com/api/webhooks/1074044242013458446/xVYIlONpDg6r1ndqb5eHTKA2v_cVs48mefh4IByQy6MAUCo4vIL14gRUSCvamxJOWSyv

Gửi tin nhắn vào channel discord (ID trong URI bên trên) với nội dung bất kỳ.

Với format body của request do discord chỉ định:

HTTP POST

```json
{
  "content": "Hello everybody 😅 😂 🤣 =))"
}
```

<details>
  <summary>Đáp án</summary>
  
  ```javascript
 async function sendMessage() {
    await fetch(
        `https://discord.com/api/webhooks/1081406356084502528/Rhg1nyvAXBt6rq83_K8WNd3TJPC2UafqIDh8r9xujWiTm1wNd172sMNG51Jdx0k1e8Rn`
        , {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                "content": "Hello everybody 😅 😂 🤣 =))"
            })
        });
};
sendMessage();
  ```
</details>

# Phần 3: Vẫn là HTTP nhưng với những endpoint được bảo mật với token

**Câu 7:**

Tính phí giao hàng tại Việt Nam khi mua hàng online bằng API của cty chuyển phát nhanh (GHN)

Tự tạo tài khoản để lấy token hoặc sử dụng token có sẵn `0d1b456f-8b24-11eb-8be2-c21e19fc6803`

Dựa vào tài liệu của cty tại https://api.ghn.vn/home/docs/detail?id=76 hãy tính cước phí
vận chuyển kiện hàng nặng 2kg, length = 50cm, width=40cm, height=30cm từ Phường Phạm Ngũ Lão, quận 1,
HCM đến phường Thanh Trì

# Phần 4: Xử lý data realtime với giao thức websocket (Optional)

**Câu 8:**

Giá bitcoin sàn binance **wss://stream.binance.com:9443/ws/btcusdt@trade**

Tạo kết nối và `console.log` giá bitcoin.
