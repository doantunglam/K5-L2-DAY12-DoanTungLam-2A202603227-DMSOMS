# Danh sách lớp v0 — Doãn Tùng Lâm · G10

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person (seat=driver) | driver | Xác định đúng người lái để mọi cảnh báo áp lên đúng người | Có (hình dạng thân người) |
| 2 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Nhắc thắt dây an toàn, phát hiện đeo sai | Có khi dải dây không chìm trong bóng tối |
| 3 | face (box) | có / không | Làm vùng gốc để tìm mắt, đầu, hướng nhìn | Có, trừ khi mặt quay đi hoặc bị tay che |
| 4 | eye_left / eye_right | open / closed / unknown | Phát hiện buồn ngủ (mắt nhắm lâu) | Có, trừ khi kính phản xạ hoặc mắt bị che |
| 5 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện mất tập trung (không nhìn đường) | Phụ thuộc vào thấy mắt và đầu |
| 6 | hand (on_wheel) | yes / no / unknown | Biết tay có đang điều khiển xe không; xe tự lái thì no là bình thường | Có (hình dạng bàn tay) |
| 7 | phone (state) | held / mounted / lap | Phát hiện dùng điện thoại khi lái | Có khi thấy cạnh hoặc màn hình |
| 8 | face13 (13 điểm) | điểm + cờ occluded / outside | Ước lượng tư thế đầu và trạng thái mắt chính xác hơn | Có khi mặt đủ rộng và rõ |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person (seat) | rear_left / rear_middle / rear_right / front_passenger | Đếm người và biết ngồi ghế nào để điều chỉnh túi khí và nhắc dây an toàn | Có (hình dạng) |
| 2 | seatbelt | not_worn / unknown (ảnh SVIRO) | Nhắc thắt dây cho hành khách | Chỉ khi thấy dải dây; ảnh tối thì unknown |
| 3 | face (box) | có / không | Xác nhận có mặt người, hỗ trợ phân biệt người với vật | Có khi mặt hướng về camera |
| 4 | infant_seat (facing) | rear / front, theo ghế | Nhắc quên trẻ trong xe; tắt túi khí ghế trước | Có (hình dạng và quai xách) |
| 5 | child_seat (occupied) | unknown / no / yes | Nhận biết ghế trẻ em và ghế đang trống hay có người | Có (hình dạng) |
| 6 | object (type) | other / bag / box / cup | Nhắc quên đồ; tránh nhầm vật với người | Có (hình dạng) |
| 7 | frame_meta | modality, light, camera_blocked | Lọc ảnh theo điều kiện chiếu sáng và camera bị che khi huấn luyện | Có (thuộc tính của khung) |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: Búp bê hoặc em bé giả nằm trong ghế em bé thì gán `person` kèm `face` hay gán `object` kèm box ghế? Guideline chỉ nói "vật trong ghế trẻ em có hai box", chưa nói búp bê tính là vật hay người.
   Khung ví dụ: S03_rgb, S05_rgb, S07_rgb
   Bạn tạm gán thế nào và vì sao: Tạm gán theo hình dạng thấy được là một người nhỏ (`person`) kèm box ghế, vì model OMS cần nhận ra có trẻ trong xe. Chờ xác nhận.
2. Câu hỏi: Khi tài xế nhắm mắt hoặc mặt bị che, `gaze_zone` nên ghi `other` hay `lap`? Guideline chỉ nói "không chắc thì other".
   Khung ví dụ: D02, D04
   Bạn tạm gán thế nào và vì sao: Tạm ghi `other` vì không xác định được hướng nhìn khi mắt nhắm; nếu hướng đầu nghiêng xuống rõ thì có thể là `lap`. Chờ xác nhận.
