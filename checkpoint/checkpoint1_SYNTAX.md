# Apps for self learning

 1. [exercism.org](https://exercism.org/tracks/javascript/concepts)
 2. [Learn Javascript](https://play.google.com/store/apps/details?id=js.javascript.web.coding.programming.learn.development)
 3. [Learn Coding/Programming: Mimo](https://play.google.com/store/apps/details?id=com.getmimo) (frontend + backend)
 4. [sololearn](https://play.google.com/store/apps/details?id=com.sololearn)
 _______________
 5. [codecombat.com](https://codecombat.com/play/dungeon)  (learn OOP if you want).
 6. [Programming Hero: Coding Fun](https://play.google.com/store/apps/details?id=com.learnprogramming.codecamp) (Learn [ReactJS](https://reactjs.org/) if you want).

P/S: *You can use bluestack or VPN if the app doesn't support in your country.*

# Phần 1: Thao tác mảng (Array Built-in Methods)

> Chuẩn bị:
>
> - Callback là gì?
> - Prototype là gì?
> - OOP là gì?
> - Syntax mới ES6: arrow function

---

> Mục tiêu:
>
> - Phân biệt được imutable và mutable method.
> - Phân biệt được imperative programming và declarative programming.

---

**Input for client:** _server (backend) response :_

```json
[
  {
    "studentID": 111,
    "weight": 85,
    "height": 170
  },
  {
    "studentID": 122,
    "weight": 65,
    "height": 150
  },
  {
    "studentID": 133,
    "weight": 120,
    "height": 182
  }
]
```

**Câu 1:**

_Client (frontend) expect:_

```javasctipt
[
  {
    studentID: 111,
    BMI: 29
  },
  {
    studentID: 122,
    BMI: 28
  },
  {
    studentID: 133,
    BMI: 36
  }
]
```

Công thức tính BMI = weight / ( height \*\* 2 )

---

<details>
  <summary>Đáp án</summary>

  ```javascript
  const data = [     // Khởi tạo nơi chứa data (JSON) do server response
    {
        studentID: 111,
        weight: 85,
        height: 170
    },
    {
        studentID: 122,
        weight: 65,
        height: 150
    },
    {
        studentID: 133,
        weight: 120,
        height: 182
    }
]

// Cách viết 1: Viết trực tiếp callback vào param của map (tên hàm BMIcaculate có thể không cần thiết)
const cach1 = data.map(function BMIcaculate(stu) {
    return ({
        studentID: stu.studentID,
        BMI: stu.weight / ((stu.height / 100) ** 2)
    })
});
console.log("viết kiểu 1", cach1);



// Cách viết 2: Khai báo callback bên ngoài sau đó truyền vào param
// cần khai báo BMIcaculate để truyền vào => "best practice"
function BMIcaculate(stu) {
    return ({
        studentID: stu.studentID,
        BMI: stu.weight / ((stu.height / 100) ** 2)
    })
};
const cach2 = data.map(BMIcaculate); //Chỉ cần nhìn vào cách đặt tên hàm, không cần đọc nội dung bên trong hàm (body của hàm) vẫn có thể hiểu mục đích của dòng code này.
console.log("viết kiểu 2", cach2);
 
 
 

// Cách viết 3: anonymous function (không cần đặt tên cho hàm)
// Thường dùng đối với hàm có logic đơn giản, ngắn
const cach3 = data.map(function (stu) {
    return ({
        studentID: stu.studentID,
        BMI: Math.floor(stu.weight / ((stu.height / 100) ** 2)) // làm tròn số
    })
});
console.log("viết kiểu 3", cach3);
 
 
 

// Cách viết 4: anonymous function với cú pháp arrow function
// Sau năm 2015 thường dùng syntax arrow function
const cach4 = data.map(stu => ({
    studentID: stu.studentID,
    BMI: Math.floor(stu.weight / ((stu.height / 100) ** 2))
  })
);
 // Chỉ có 1 parameter nên không cần dấu đóng mở ngoặc trước và sau stu
 // trong trường hợp này dấu => có ý nghĩa là return
 // Do không có thân hàm, return trực tiếp giá trị nên cặp ngoặc body function {} bị lược bỏ.
console.log("viết kiểu 4", cach4);


  ```
</details>

**Câu 2:**

_Client (frontend) expect:_ Mảng chỉ chứa student cao hơn 1,65m.

```javasctipt
[
  {
    studentID: 111,
    weight: 85,
    height: 170
  },
  {
    studentID: 133,
    weight: 120,
    height: 182
  }
]
```

**Câu 3:**
Tìm student có mã số sinh viên là: 122

_Client (frontend) expect:_

```javascript
{
  studentID: 122,
  weight: 65,
  height: 150
}
```

**Câu 4**:
Sắp xếp list theo thứ tự cân nặng tăng dần

_Client (frontend) expect:_

```javasctipt
[
  {
    studentID: 122,
    weight: 65,
    height": 150
  },
  {
    studentID: 111,
    weight: 85,
    height: 170
  },
  {
    studentID: 133,
    weight: 120,
    height: 182
  }
]
```

**Câu 5**:
Thêm 1 student vào list.

**Câu 6**:
Tính chiều cao trung bình của cả lớp.

_Client (frontend) expect:_

```
1.673
```

**Câu 7**:

**Input for client:** _server (backend) response :_

```json
{
  "id": 0,
  "name": "Iphone 14 pro max",
  "brand": "Apple",
  "fake_price": 99999999,
  "real_price": 88888888,
 "description": "Iphone USA made in china",
  "cpu": "M2",
  "gpu": "M2",
  "ram": 128,
  "memory": 256,
  "screen_size": "10",
  "battery": 70000,
  "front_camera": 20,
  "rear_camera": 30,
  "release_year": 2022,
  "sim": 4
}
```

_Client (frontend) expect:_

```javasctipt
{
  id: 0,
  name: "Iphone 14 pro max",
  brand: "Apple",
  fake_price: 99999999,
  real_price: 88888888,
  description: "Iphone USA made in china",
  cpu: "M2",
  gpu: "M2",
  ram: 128,
  memory: 256,
  screen_size: "10",
  battery: 70000,
  front_camera: 20,
  rear_camera: 30,
  release_year: 2022,
  sim: 4,
  color: "yellow" //  <===Thêm thuộc tính màu sắc
}
```

**Câu 8:**

**Input for client:**

- Server 1 (đặt ở Mỹ) response 2 mảng:

```json
[
  {
    "productID": 111,
    "name": "jacket",
    "brandID": 333,
    "OriginOfGoods": "DE"
  },
  {
    "productID": 156,
    "name": "T-shirt",
    "brandID": 344,
    "OriginOfGoods": "VN"
  },
  {
    "productID": 198,
    "name": "yellow suit",
    "brandID": 334,
    "OriginOfGoods": "JP"
  }
]
```

và

```json
[
  {
    "brandID": 333,
    "name": "puma"
  },
  {
    "brandID": 344,
    "name": "adidas"
  },
  {
    "brandID": 334,
    "name": "ZARA"
  }
]
```

- Server 2 (đặt ở Nhật) response :

```json
[
  {
    "countryCode": "DE",
    "countryName": "Germany"
  },
  {
    "countryCode": "VN",
    "countryName": "Vietnam"
  },
  {
    "countryCode": "JP",
    "countryName": "Japan"
  },
  {
    "countryCode": "OTHER",
    "countryName": "other country"
  }
]
```

_Client (frontend) expect:_

```javasctipt
[
  {
    productID: 111,
    name: "jacket",
    brand: "puma",
    OriginOfGoods: "Germany"
  },
  {
    productID: 156,
    name: "T-shirt",
    brand: "adidas",
    OriginOfGoods: "Vietnam"
  },
  {
    productID: 198,
    name: "yellow suit",
    brand: "ZARA",
    OriginOfGoods: "Japan"
  }
]
```

**Câu 9**:
**Input for client:** Cho API data chứng khoán sàn HOSE như sau:
https://finfo-api.vndirect.com.vn/v4/stock_prices?sort=date%3Adesc&q=floor%3AHOSE%2CHNX~type%3ASTOCK&fields=code%2Cdate%2Copen%2Chigh%2Clow%2Cclose%2CnmVolume%2Cchange%2CpctChange&size=100000&page=1

_Client (frontend) expect:_
Tính tổng `nmVolume` của các cty có mã cổ phiếu bắt đầu bằng ký tự `V`.

**Câu 10**:

**Input for client:** _server (backend) response :_

```json
[
  {
    "Name": "C#",
    "InfluencedBy": ["C++", "VB", "Pascal"],
    "backer": {
      "name": "Microsoft",
      "Founded": 1975,
      "Address": {
        "City": "Washington",
        "District": "Redmond"
      }
    }
  },
  {
    "Name": "Java",
    "InfluencedBy": ["C++", "Objective-C", "Pascal"],
    "backer": {
      "name": "Oracle",
      "Founded": 1900,
      "Address": {
        "City": "Ohio",
        "District": "Hello"
      }
    }
  },
  {
    "Name": "Javascript",
    "InfluencedBy": ["HyperTalk"],
    "backer": {
      "name": "ECMAScript",
      "Founded": 1995,
      "Address": {
        "City": "Washington",
        "District": "Redmond"
      }
    }
  }
]
```

_Client (frontend) expect:_

- Sắp xếp mảng theo năm thành lập tăng dần.
- Tìm những object có trụ sở cty tại `Washington`.

# Phần 2: phân biệt tham chiếu & tham trị (Python, C#, java, C++, ... tương tự)

> Chuẩn bị:
>
> - Ngôn ngữ lập trình có mấy loại kiểu dữ liệu?
> - Phạm vi hoạt động (scope) của biển trong các ngôn ngữ lập trình?
> - Phân biệt shallow copy và deep copy.
> - Phân biệt truyền tham số kiểu tham chiếu (pass by vaule) và truyền tham số kiểu tham trị (pass by reference) vào một function.
> - Nâng cao: Phân biệt ô nhớ stack và heap.

---

**Câu 11:** Thực tế không ai viết như này, sẽ có cách riêng để clone 2 mảng)

```javascript
let arr1 = [1, 2, 3];
let arr2 = arr1;

arr2[0] = 0;
console.log(arr1);
```

Đoạn code trên in ra gì? Tại sao?

**Câu 12**: (Thực tế không ai viết như này, sẽ có cách riêng để clone 2 mảng)

```javascript
let arr1 = [1, 2, 3];
let arr2 = arr1;

arr2 = [4, 5, 6];

console.log(arr1);
```

Đoạn code trên in ra gì? Tại sao?

**Câu 13.1**: (Thực tế không ai viết như này)

```javascript
let a = 1;

function func(a) {
  a = 2;
}

func(a);
console.log(a);
```

Đoạn code trên in ra gì? Tại sao?

**Câu 13.2**: (Trường hợp này có trong thực tế nhưng hạn chế viết như này)

```javascript
let a = 1;

function func() {
  a = 2;
}

func();
console.log(a);
```

Đoạn code trên in ra gì? Tại sao?

**Câu 14:** (Trường hợp này có trong thực tế nhưng hạn chế viết như này)

```javascript
const a = [1, 2, 3];

function func(a) {
  a[0] = 0;
}

func(a);

console.log(a);
```

Đoạn code trên in ra gì? Tại sao?

**Câu 15:** (Thực tế không ai viết như này)

```javascript
let a = [1, 2, 3];

function func(a) {
  a = [4, 5, 6];
}

func(a);

console.log(a);
```

Đoạn code trên in ra gì? Tại sao?

---

## Conclusion: 

Trong thực tế truyền tham chiếu dễ gây side-effect nên JS hạn chế truyền kiểu này. Thư viện immerJS (Tiếng Đức nghĩa là: Luôn luôn) hoặc ImmuatableJS của facebook giúp khắc phục vấn đề này.

Có 2 kiểu function:
- Pure function 
- Side Effect function (còn gọi là impure function)

Nếu function không có yếu tố bên ngoài (Gọi API OS, web API, DOM, user input....) thì ưu tiên viết pure function.
