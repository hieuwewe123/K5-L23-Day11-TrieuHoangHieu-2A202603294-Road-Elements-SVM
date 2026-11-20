# Phiếu QC 1 — Road v1.0

**Lô được kiểm:** Hà Huy Dũng (`hahuydung`)<br>
**Người kiểm:** Triệu Hoàng Hiếu<br>
**Ngày:** 20/11/2026<br>
**File:** `hahuydung-front.zip`, `hahuydung-fisheye.zip`, manifest revision 1. Hai SHA-256 khớp với manifest.<br>
**Mẫu kiểm bằng ảnh gốc và lớp nhãn:** A01, A04, A07, A08, A09, B03. Tổng cộng 6 ảnh bắt buộc, 0 ảnh thêm, **71 nhãn** (47 shape + 24 tag). Lint chạy riêng trên toàn bộ 28 ảnh.

## Tổng hợp theo mã

| Mã | Mục kiểm | Số mục kiểm | Số lỗi ghi nhận | Mức lỗi ghi nhận |
| --- | --- | ---: | ---: | --- |
| QC1-01 | Tag camera | 6 ảnh | 0 | — |
| QC1-02 | Vạch L1/R1 nhìn thấy được | 6 ảnh | 0 | — |
| QC1-03 | Position | 19 lane | 0 | — |
| QC1-04 | Tâm vạch, chiều, điểm dừng | 19 lane | 4 | Chính |
| QC1-05 | Nối vạch đứt và chỗ che | 19 lane | 0 | — |
| QC1-06 | Style, color, kind | 19 lane | 0 | — |
| QC1-07 | Vùng lái | 13 drivable | 0 | — |
| QC1-08 | Cụm đèn, màu đang sáng | 13 traffic_light | 0 | — |
| QC1-09 | Facing, type, group, biển phụ | 15 đèn/biển | 0 | — |
| QC1-10 | Đối chiếu biển thật, độ đầy đủ | 6 ảnh | 0 | — |
| QC1-11 | Quy tắc fisheye | 5 shape trên B03 | 0 | — |
| QC1-12 | File và manifest | 2 ZIP + 1 manifest | 0 | — |

Số 0 nghĩa là chưa ghi nhận lỗi chắc chắn ở mục đó trong mẫu. Phạm vi nhãn theo ảnh cần đối chiếu với bảng kế hoạch lab nếu có.

## Danh sách lỗi

| # | Mã | Ảnh | Nhãn và tọa độ điểm đầu | Mức | Mô tả |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-04 | A01 | lane R2, (1280, 704) | Chính | Điểm tại (901, 621) nằm thấp hơn tâm vạch vàng trong ảnh gốc khoảng 10 px. Rà lại đoạn giữa và đưa điểm lên tâm vệt sơn. |
| 2 | QC1-04 | A01 | lane R1, (703, 720) | Chính | Ở đáy ảnh, polyline kéo xuống dưới đoạn sơn cuối còn nhận ra quanh (650, 680). Dừng tại phần vạch còn thấy thay vì kéo qua vùng tối đến mép ảnh. |
| 3 | QC1-04 | A08 | lane L2, (0, 361) | Chính | Đoạn đầu đi dọc vạch dừng ngang ở góc trái rồi chuyển sang vạch dọc. Bỏ đoạn ngang và bắt đầu trên tâm vạch dọc nhận diện được. |
| 4 | QC1-04 | A08 | lane R1, (738, 415) | Chính | Điểm đầu bỏ mất đoạn vạch trắng gần nhất, còn thấy ở khoảng (757, 440), ngay trước vạch qua đường. Bổ sung đoạn còn thấy và đặt điểm trên tâm sơn. |

## Ca mơ hồ và cảnh báo lint

- Lint báo A05 thiếu L1/R1, A06 thiếu R1 và A09 thiếu R1. README của người nộp ghi coach đã cho miễn cả 4 cảnh báo. Phiếu này ghi nhận thông tin do người nộp cung cấp. A09 có trong mẫu; phần phải của làn không đủ rõ để kết luận thiếu nhãn.
- Ở A07, cần phân biệt vạch trắng rất mờ và dải sáng sát chân dải chắn trước khi chốt L1. Chưa tính lỗi cho trường hợp này.

## Quyết định

**Lỗi nặng:** 0 xác nhận trong mẫu. **Lỗi chính:** 4 / 71 = **5,63%**. **Lỗi nhẹ:** 0 ghi nhận. **Ca cần đối chiếu thêm:** 1 (A07).<br>
**Quyết định: Rework.** Tỉ lệ lỗi chính vượt 5%. Sửa bốn vị trí trong bảng rồi rà lại lớp phủ trên ảnh gốc trước khi gửi bản tiếp theo.
