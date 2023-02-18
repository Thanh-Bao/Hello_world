### Phần 1: Những thẻ có tần suất xuất hiện nhiều trong web

|     | tag                           | name     | default |
| --- | ----------------------------- | -------- | ------- |
| 1   | `<div>`                       | division | block   |
| 2   | `<span>`                      |          | inline  |
| 3   | `<a>`                         | anchor   | inline  |
| 4   | `<img>`                       | image    | inline  |
| 5   | `<button>`                    |          | inline  |
| 5   | `<input>`, `<select>`, `<ul>` |          | inline  |

---

|     |                                              |                                                              |
| --- | -------------------------------------------- | ------------------------------------------------------------ |
| 1   | [htmlreference.io](https://htmlreference.io) | kiểm tra một thẻ là `inline` hay `block`                     |
| 2   | [caniuse.com](https://caniuse.com/)          | kiểm tra một thuộc tính css có tương thích với browser không |

### Phần 2: CSS

#### 2.1. Box model

- https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model#what_is_the_css_box_model
- https://www.youtube.com/watch?v=rIO5326FgPE&ab_channel=WebDevSimplified

---

#### 2.2. layout with flexbox (cũng là layout mặc định react native - mobile app)

Layout trên mặt phẳng Oxy. Chỉ có tác dụng với thẻ `block`. 
Game luyện phản xạ CSS:

- [https://flexboxfroggy.com](https://flexboxfroggy.com/)
- [https://courses.cs.washington.edu/courses/cse154/flexboxducky](https://courses.cs.washington.edu/courses/cse154/flexboxducky)
- [https://mastery.games/flexboxzombies](https://mastery.games/flexboxzombies) ( luyện phản xạ với thuộc tính `flex-start`, `flex-end` của`justify-content`, `align-items`)
- [http://www.flexboxdefense.com](http://www.flexboxdefense.com/)
- [https://codingfantasy.com/games/flexboxadventure](https://codingfantasy.com/games/flexboxadventure)
- [https://knightsoftheflexboxtable.com](https://knightsoftheflexboxtable.com/) (game luyện tập flexbox với thư viện [tailwind css](https://tailwindcss.com/)

#### 2.3. Thuộc tính position (layout theo trục Oz)

- https://www.tutorialbrain.com/css_tutorial/css_position/
- https://developer.mozilla.org/en-US/docs/Web/CSS/position

Ứng dùng làm popup, dialog, cố định navigtion bar, sidebar, ...khi scroll chuột.

### Phần 3: Thư viện CSS

|     | Name      | link             | sponsor          | Installation guide                                                        |
| --- | --------- | ---------------- | ---------------- | ------------------------------------------------------------------------- |
| 1   | tailwind  | tailwindcss.com  | VueJS, NAPI, ... | https://tailwindcss.com/docs/installation/play-cdn                        |
| 2   | bootstrap | getbootstrap.com | Twitter          | https://getbootstrap.com/docs/5.3/getting-started/introduction/#cdn-links |

### Phần 4: Thực hành

Clone một trong những trang web sau

|     | URL                                    | traffic/month | library |
| --- | -------------------------------------- | ------------- | ------- |
| 1   | [yahoo.co.jp](https://yahoo.co.jp)     | 2B            | reactJS |
| 2   | [rakuten.co.jp](https://rakuten.co.jp) | 500M          | reactJS |
| 3   | [fc2.com](https://fc2.com)             | 300M          | reactJS |
| 4   | [livedoor.com](https://livedoor.com)   | 100M          | reactJS |
