# Báo cáo cá nhân — Ngày 11 (bản nháp)

Họ tên: Triệu Hoàng Hiếu<br>
Mã học viên: 2A202603294<br>
CVAT: 2.81.0<br>
Guideline: Road v1.0<br>
Manifest: revision 3 (sau rà bổ sung)

## 1. Kiểm project

Đã đối chiếu trong CVAT local: đúng 6 label, kiểu hình, thuộc tính và 4 tag. Cả 28 ảnh đã có đủ 4 tag.

## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 26 | 3 | 3 | 6 | 19 | 7 |
| front-extra | 4 | 8 | 0 | 0 | 0 | 5 | 3 |
| fisheye | 8 | 2 | 2 | 4 | 3 | 2 | 0 |
| fisheye-extra | 4 | 0 | 0 | 3 | 1 | 0 | 0 |

## 3. Ca khó và điểm cần rà

- Chưa có bảng yêu cầu từng ảnh trong slide. Set A dựa trên guideline và checkpoint. Set B dựa thêm vào manifest ứng viên.
- Tọa độ bản nháp được ước lượng qua ảnh thu nhỏ. Cần rà tâm vạch và kích thước hộp ở ảnh gốc trước khi duyệt.
- Đã rà 7 ảnh ở độ phân giải gốc và bổ sung L1 cho A06 và A12. QC1-02 vẫn báo A05, A06, A07, A12 và A14 vì các vạch còn thiếu không đủ rõ để gán. Kết quả tự rà chi tiết ở bảng dưới.
- B11 chỉ có tag vì vùng thấy rõ chủ yếu là ô đỗ. B06/B08 cần rà lại vạch dọc và phạm vi vùng lái. B02 cần rà hướng mặt đèn và edge_zone.

| Ảnh | Vạch lint báo thiếu | Kết quả tự rà |
| --- | --- | --- |
| A05 | L1, R1 | Mặt đường không có vạch phân làn đủ rõ. |
| A06 | R1 | Phía phải thấy vạch qua đường và mép đường. Chưa phân biệt được một R1 dọc đủ rõ. |
| A07 | L1 | Rìa trái là dải chắn bê tông. Chưa thấy vạch sơn trái đủ rõ. |
| A12 | R1 | Sau vạch qua đường chưa thấy vạch dọc bên phải đủ rõ. |
| A14 (thêm) | R1 | Cảnh đêm và xe phía trước che khuất. Chưa thấy R1 đủ rõ. |

Giữ nguyên hình khi không xác định được tâm vạch. Lint revision 2 vẫn liệt kê 6 cảnh báo vì không xét ảnh gốc. Bảng này ghi kết quả tự rà, chưa có xác nhận miễn lỗi theo đặc tả bàn giao trong repo.

## 4. Phiếu QC 1 nhận được

Hà Huy Dũng kiểm revision 1 và kết luận **Rework** (2 lỗi nặng, 8 lỗi chính trên 52 nhãn). Phiếu mình lập cho lô của Dũng nằm ở `trieuhoanghieu-qc1-for-hahuydung.md`. Mẫu mình kiểm gồm 6 ảnh A01–A06, tổng cộng 51 nhãn. Ghi nhận 3 lỗi chính (5,88%) và kết luận Rework.

| Mã | Số lỗi | Đã sửa trong revision 2 |
| --- | ---: | --- |
| QC1-02 | 2 | Thêm L1 A08 và R1 A10. Bật occluded cho R1 A10. |
| QC1-04 | 4 | Đặt lại tâm L2 A01. Thêm L2 ở A08/A10 và R2 ở B03. |
| QC1-08 | 1 | Thêm cụm đèn xanh được chỉ ra tại A08 và các cụm đèn phụ được nêu cùng nhận xét. |
| QC1-10 | 1 | Tách hai biển cấm ở A10 thành các hộp riêng. |
| QC1-11 | 2 | Bổ sung điểm bám cung cho R1 B03 và rút ngắn road_curb B05. |

Ba ca mơ hồ trong phiếu (L1 xa ở B03, road_curb A10 và weather B05) vẫn là mục cần đối chiếu. Đã lưu bản cũ trong `out/r1/`.

**Revision 3:** Căn lại R1 A02 theo tâm vạch trắng. Căn lại R1 A04 và ranh giới chung của hai vùng drivable.

## 5. Kiểm file

Hai ZIP đọc được bằng lint và chỉ chứa annotations.xml. Manifest được tạo từ hai ZIP. Còn 6 cảnh báo QC1-02. Hai ZIP lấy từ export CVAT for images 1.1 và gộp phần extra theo từng bộ ảnh.

| File | Mở lại được | Ảnh 1, số shape CVAT / ZIP | Ảnh 2, số shape CVAT / ZIP | Tag camera |
| --- | --- | --- | --- | --- |
| trieuhoanghieu-front.zip | Có | A01: 9 / 9 | A02: 3 / 3 | Có trên mọi ảnh |
| trieuhoanghieu-fisheye.zip | Có | B01: 1 / 1 | B02: 2 / 2 | Có trên mọi ảnh |

## 6. Ảnh chụp màn hình

Bốn ảnh minh chứng được giữ trong gói nộp riêng để bàn giao qua kênh lớp. Các thay đổi revision 2 được ghi ở mục 4.





## 7. Tự đánh giá

Nếu polyline dừng trước phần vạch vẫn còn nhìn thấy, các hàng row-anchor phía trên điểm dừng có thể bị đánh dấu là không có làn. Khi rà lại, kiểm tra điểm cuối của từng vạch trên ảnh gốc.
