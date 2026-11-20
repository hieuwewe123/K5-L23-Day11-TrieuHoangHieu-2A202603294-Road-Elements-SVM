# Phiếu QC 1 — Road v1.0

**Lô được kiểm:** Hà Huy Dũng (`hahuydung`)<br>
**Người kiểm:** Triệu Hoàng Hiếu<br>
**Ngày:** 20/11/2026<br>
**File:** `hahuydung-front.zip`, `hahuydung-fisheye.zip`, manifest revision 1. Hai SHA-256 khớp với manifest.<br>
**Mẫu kiểm bằng ảnh gốc và lớp nhãn:** A01, A02, A03, A04, A05 và A06. Tổng cộng 6 ảnh bắt buộc, 0 ảnh thêm, **51 nhãn** (27 shape + 24 tag). Lint chạy riêng trên toàn bộ 28 ảnh.

## Tổng hợp theo mã

| Mã | Mục kiểm | Số mục kiểm | Số lỗi ghi nhận | Mức lỗi ghi nhận |
| --- | --- | ---: | ---: | --- |
| QC1-01 | Tag camera | 6 ảnh | 0 | — |
| QC1-02 | Vạch L1/R1 nhìn thấy được | 6 ảnh | 0 | — |
| QC1-03 | Position | 14 lane | 0 | — |
| QC1-04 | Tâm vạch, chiều, điểm dừng | 14 lane | 3 | Chính |
| QC1-05 | Nối vạch đứt và chỗ che | 14 lane | 0 | — |
| QC1-06 | Style, color, kind | 14 lane | 0 | — |
| QC1-07 | Vùng lái | 11 drivable | 0 | — |
| QC1-08 | Cụm đèn, màu đang sáng | 6 ảnh, 0 hộp đèn hiện có | 0 | — |
| QC1-09 | Facing, type, group, biển phụ | 0 hộp đèn/biển | 0 | — |
| QC1-10 | Đối chiếu biển thật, độ đầy đủ | 6 ảnh | 0 | — |
| QC1-11 | Quy tắc fisheye | 0 ảnh fisheye (ngoài mẫu) | 0 | — |
| QC1-12 | File và manifest | 2 ZIP + 1 manifest | 0 | — |

Số 0 nghĩa là chưa ghi nhận lỗi chắc chắn ở mục đó trong mẫu. Phạm vi nhãn theo ảnh cần đối chiếu với bảng kế hoạch lab nếu có.

## Danh sách lỗi

| # | Mã | Ảnh | Nhãn và tọa độ điểm đầu | Mức | Mô tả |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-04 | A01 | lane R2, (1280, 704) | Chính | Điểm tại (901, 621) nằm thấp hơn tâm vạch vàng trong ảnh gốc khoảng 10 px. Rà lại đoạn giữa và đưa điểm lên tâm vệt sơn. |
| 2 | QC1-04 | A01 | lane R1, (703, 720) | Chính | Ở đáy ảnh, polyline kéo xuống dưới đoạn sơn cuối còn nhận ra quanh (650, 680). Dừng tại phần vạch còn thấy thay vì kéo qua vùng tối đến mép ảnh. |
| 3 | QC1-04 | A02 | lane L1, (381, 720) | Chính | Đường kéo xuống mép dưới qua vùng bóng đổ. Vệt sơn gần nhất nhận ra chỉ nằm quanh (512, 568). Rà lại đầu polyline và dừng tại vệt sơn thấy được. |

## Ca mơ hồ và cảnh báo lint

- Lint báo A05 thiếu L1/R1, A06 thiếu R1 và A09 thiếu R1. README của người nộp ghi coach đã cho miễn cả 4 cảnh báo. Phiếu này ghi nhận thông tin do người nộp cung cấp. A05 và A06 nằm trong mẫu. A09 nằm ngoài mẫu.
- A06 có cụm đèn thấy trên ảnh. Cần đối chiếu bảng yêu cầu của slot A06 trước khi tính lỗi thiếu nhãn đèn. Chưa tính lỗi.
- Ảnh đối chiếu không ghi nhận lỗi trong mẫu: A04.

## Quyết định

**Lỗi nặng:** 0 xác nhận trong mẫu. **Lỗi chính:** 3 / 51 = **5,88%**. **Lỗi nhẹ:** 0 ghi nhận. **Ca cần đối chiếu thêm:** 1 (A06).<br>
**Quyết định: Rework.** Tỉ lệ lỗi chính vượt 5%. Sửa ba vị trí trong bảng rồi rà lại lớp phủ trên ảnh gốc trước khi gửi bản tiếp theo.
