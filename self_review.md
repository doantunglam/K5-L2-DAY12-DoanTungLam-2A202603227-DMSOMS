# Tự đánh giá — Doãn Tùng Lâm · G10

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_ir | object (đầu tiên tôi vẽ là điện thoại) | wrong_class / extra | Nhầm móc ISOFIX phát sáng đỏ trên ghế giữa là điện thoại; đã xóa box | Đã sửa |
| S01_rgb | face, object | missing | Ban đầu chỉ có person, thiếu box face và các vật vì ảnh RGB tối; sau khi tăng brightness mới thấy | Đã sửa |
| D03 | hand | missing | Thiếu box hand so với bản Tuấn Anh | Đã sửa |
| D04 | hand (side, on_wheel) | lr_flip / guess | Gán ngược trái/phải của hai tay trên ảnh xoay 90°; on_wheel để unknown trong khi đúng là no | Đã sửa |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Nhầm trái/phải của người trên ảnh DMS xoay 90° (D04, hai hand bị gán ngược `side`).

Vì sao mình mắc: Nhìn theo hướng trái/phải của ảnh thay vì theo người, mà ảnh Drive&Act bị xoay nên mất mốc quen thuộc.

Lần sau tránh bằng cách: Trước khi gán `side`, xác định hướng đầu của tài xế, nhớ rằng mắt trái có y lớn hơn trên ảnh D##, rồi suy ra tay trái/phải của người; sau đó đối chiếu lại bằng `diff` với bạn.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai (D04, hai `hand` `side`, và `on_wheel`). Mình học được: trái/phải phải gán theo người chứ không theo ảnh, và khi tay không rõ vẫn có thể gán `no` cho `on_wheel`.
