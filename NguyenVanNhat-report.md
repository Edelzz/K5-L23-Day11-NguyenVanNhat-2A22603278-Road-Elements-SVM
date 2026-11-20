# Báo cáo cá nhân — Ngày 11

- Họ tên: Nguyễn Văn Nhất
- Mã học viên: 2A22603278 (theo tên thư mục bài lab, cần đối chiếu)
- Phiên bản: CVAT local 2.81.0, Guideline Road v1.0
- Manifest: revision 1. Chưa nộp lại sau Rework.
- Thời điểm export: 20/11/2026, 18:41 (giờ Việt Nam, theo metadata CVAT)

## 1. Kiểm project

| Mục | Kết quả | Ghi chú |
| --- | --- | --- |
| Sáu nhãn vẽ và kiểu hình | Khớp | Đối chiếu metadata của hai ZIP với cấu hình Road v1.0 |
| Thuộc tính và các giá trị | Khớp | Đối chiếu tên, kiểu nhập và danh sách giá trị |
| Bốn tag ảnh | Đủ 20/20 ảnh | `camera`, `timeofday`, `weather`, `source` |

Kết thúc polyline bằng phím **N** theo hướng dẫn lab. Đặt tag bằng công cụ **Tag**, rồi vào **Objects → Details** để chỉnh thuộc tính `value`.

## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 25 | 11 | 5 | 21 | 34 | 46 |
| front-extra (0/4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| fisheye | 8 | 6 | 2 | 11 | 2 | 10 | 11 |
| fisheye-extra (0/4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

## 3. Bảng ca khó

| Ảnh | Nhãn | Phân vân giữa | Đã chọn trong bản export | Lý do |
| --- | --- | --- | --- | --- |
| A05 | lane | Vạch sơn hay mép đường bị xe đỗ che | Chưa gán L1/R1 | Không xác định được vệt sơn tương ứng. Chờ coach xác nhận QC1-02. |
| A06, A07, A08 | lane | Vạch mờ, bị che hoặc biên không có sơn | Chưa gán R1 ở A06 và L1 ở A07–A08 | Cần đối chiếu ảnh gốc và xác nhận với coach. |
| B03, B04 | traffic_sign | Bật hay tắt `edge_zone` | Bản export đang tắt trên hai biển bị cảnh báo | Checker đo tâm box nằm ngoài 80% bán kính. Cần rà box trên CVAT và lưu lại nếu chỉnh. |

## 4. Phiếu QC 1 nhận được

Người kiểm bài của tôi: Nguyễn Viết Minh Hoàng (2A202603281). Phạm vi kiểm: A01–A06. Kết quả của người kiểm chưa được cung cấp.

## Tự kiểm A01–A06

Đối chiếu ảnh gốc với nhãn trong `NguyenVanNhat-front.zip` (revision 1). Mẫu có **52 shape và 24 tag**, tổng cộng **76 nhãn hiện có**. Cả sáu ảnh đều có đủ bốn tag và `camera=front`.

| Ảnh | Shape + tag | Kết quả và điểm cần rà |
| --- | ---: | --- |
| A01 | 9 + 4 | Đủ L1/R1. R1 kéo tới y=720 trong XML, trong khi đoạn sơn gần xe mờ. Phóng to để xác nhận đầu polyline bám vệt sơn, nhất là phần sát đáy ảnh. |
| A02 | 6 + 4 | Đủ L1/R1. Đối chiếu ảnh thấy vạch trắng đứt ở trái và vạch trắng liền ở phải, khớp thuộc tính trong XML. |
| A03 | 10 + 4 | Đủ L1/R1. Cả hai lane đang có `occluded=0`, trong khi checkpoint A03 yêu cầu rà đoạn che. Xác định đoạn nào thật sự nối qua vật che, rồi bật cờ cho polyline tương ứng. |
| A04 | 11 + 4 | L1 là vàng liền đôi. Có một vùng `direct` và một vùng `alternative`. Checker nhắc một box biển thấp hơn 8 px (QC1-10, mức nhẹ). |
| A05 | 2 + 4 | Checker báo thiếu cả L1 và R1 (QC1-02). Trên ảnh gốc không thấy rõ vạch phân làn tương ứng. Ghi ca chờ coach xác nhận. |
| A06 | 14 + 4 | Checker báo thiếu R1 (QC1-02). Có sọc qua đường ở tiền cảnh và hàng cột bên phải. Chưa xác định được vạch R1, cần coach xác nhận. |

Lint trên mẫu trả **4 cảnh báo** gồm 3 cảnh báo nặng QC1-02 (A05: 2, A06: 1) và 1 cảnh báo nhẹ QC1-10 (A04). Tôi đã rà lại các cảnh báo và chấp nhận giữ nhãn hiện tại sau tự kiểm. Hai điểm rà bằng mắt ở A01 và A03 được ghi riêng. Các ca QC1-02 vẫn cần xác nhận của coach để áp dụng ngoại lệ khi nộp.

## 5. Kiểm file export

| File | Mở lại được? | Shape ảnh 1 (job / file) | Shape ảnh 2 (job / file) | Tag camera trong XML |
| --- | --- | --- | --- | --- |
| `NguyenVanNhat-front.zip` | Có | Chưa đếm trên giao diện / A01: 9 | Chưa đếm trên giao diện / A02: 6 | Có, `front` |
| `NguyenVanNhat-fisheye.zip` | Có | Chưa đếm trên giao diện / B01: 4 | Chưa đếm trên giao diện / B02: 10 | Có, `fisheye_front` |

Hai ZIP chỉ chứa `annotations.xml`. Lint báo 5 cảnh báo nặng QC1-02 trên A05–A08, 2 cảnh báo chính QC1-11 trên B03–B04 và 2 cảnh báo nhẹ về box thấp hơn 8 px trên A04 và B03. Khi export, cả hai job vẫn ở trạng thái `in progress`.

Tôi đã rà lại cả 9 cảnh báo và chấp nhận giữ nhãn hiện tại sau tự kiểm. Các cảnh báo vẫn xuất hiện trong kết quả lint, gồm hai nhắc nhở `edge_zone` tại B03 và B04. Kết quả tự kiểm chưa thay cho quyết định của người kiểm hoặc xác nhận ngoại lệ QC1-02 của coach.

## 6. Ảnh chụp màn hình

- [ ] Tab Labels của project.
- [ ] Ảnh A01 đã gán, có lane, vùng lái và biển.
- [ ] Ảnh B03 đã gán, phóng to đoạn polyline cong.
- [ ] Đoạn XML trong `NguyenVanNhat-front.zip` có `<polyline label="lane">`.

## 7. Tự đánh giá

QC1-02 xuất hiện nhiều nhất trong lượt tự kiểm. Ở Ngày 20, cần phóng to vùng gần xe, tìm tâm vệt sơn và ghi riêng mã ảnh thật sự không có vạch để người kiểm xác nhận.

Polyline `lane` có thể được lấy mẫu thành tọa độ x tại các hàng y để làm đích cho mô hình row-anchor. Nếu dừng polyline trước điểm xa nhất còn thấy vạch, các hàng y ở đoạn bị bỏ có thể bị gán thành “không có làn”. Chưa đối chiếu một lỗi đã sửa với phiếu QC nhận được.
