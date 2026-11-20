# Phiếu kiểm tra chất lượng lần 1 (QC 1) — Road v1.0

Lô được kiểm (học viên): Nguyễn Văn Nhất 
Người kiểm (học viên): Nguyễn Viết Minh Hoàng — 2A202603281  
Ngày kiểm: 20/11/2026  
Phiên bản hướng dẫn gán nhãn: Road v1.0  
Tệp được kiểm (tên và lần nộp `revision` trong tệp bàn giao): `NguyenVanNhat-front.zip`, revision 1 theo `NguyenVanNhat-manifest.json`.  
Mẫu đã kiểm: 6 ảnh, A01–A06. Số mục đã kiểm (hình gán nhãn và thẻ ảnh): Chưa ghi nhận.  

| Ảnh | Trạng thái kiểm |
| --- | --- |
| A01 | Đã kiểm |
| A02 | Đã kiểm |
| A03 | Đã kiểm |
| A04 | Đã kiểm |
| A05 | Đã kiểm |
| A06 | Đã kiểm |

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót |  |  | nặng |
| QC1-02 đủ L1, R1 | bỏ sót |  |  | nặng |
| QC1-03 position | sai thuộc tính / thừa |  |  | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót |  |  | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính |  |  | chính |
| QC1-06 style, color, kind | sai thuộc tính |  |  | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa |  |  | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính |  |  | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính |  |  | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi |  |  | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính |  |  | chính |
| QC1-12 file | lỗi file |  |  | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

## Trường hợp cần xác nhận

 Đã rà lại các cảnh báo lint và chấp nhận giữ nhãn hiện tại sau tự kiểm. Trong phạm vi A01–A06, lint báo thiếu L1 và R1 ở A05, thiếu R1 ở A06, và nhắc một hộp biển dưới 8 px ở A04. Các ca thiếu vạch cần coach xác nhận nếu áp dụng ngoại lệ.

| Ảnh | Câu hỏi cho người phụ trách | Trả lời (nếu có) |
| --- | --- | --- |

## Quyết định
Lỗi nặng: __   Lỗi chính: __ / __ nhãn = __ %   Lỗi nhẹ: __   Trường hợp chờ xác nhận: __  
Quyết định (Chấp nhận — Release / Tạm giữ — Hold / Yêu cầu sửa lại — Rework): Chưa kết luận.  
Lý do (theo luật của phiếu):  

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](docs/qc_severity_road_v1.0.md).
