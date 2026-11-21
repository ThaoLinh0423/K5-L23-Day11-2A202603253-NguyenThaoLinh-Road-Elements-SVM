# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Phan Thành Giáp        Người kiểm (học viên): Nguyễn Thảo Linh  
Ngày: 20/11/2026                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): phanthanhgiap-front.zip, phanthanhgiap-fisheye.zip (revision 1)  
Số ảnh kiểm: 6    Số nhãn đã kiểm (shape + tag): 100  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 12 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 16 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 16 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 16 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 16 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 14 | 2 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 6 | 1 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 16 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 10 | 1 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 0 | 0 | chính |
| QC1-12 file | lỗi file | 100 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-07 | A01 | drivable, 55 | chính | Bỏ sót vùng lái xe (drivable) |
| 2 | QC1-10 | A03 | traffic_sign | chính | Bỏ sót biển báo |
| 3 | QC1-07 | A04 | road_curb | chính | Bỏ sót đường lề (road_curb) |
| 4 | QC1-08 | A06 | traffic_light | chính | Sai màu đèn (đèn người đi bộ / facing side) |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A06 | Đèn người đi bộ hiển thị màu trắng (guideline chỉ có red, yellow, green, off, unknown) thì nên gán màu gì? | Chờ lead phản hồi |

## Quyết định
Lỗi nặng: 0   Lỗi chính: 4 / 100 nhãn = 4.0 %   Lỗi nhẹ: 0   Ca chờ lead: 1  
Quyết định (Release / Hold / Rework): Hold  
Lý do (theo luật của phiếu): Có 1 ca mơ hồ (A06) đang chờ lead trả lời; không có lỗi nặng và tỉ lệ lỗi chính là 4.0 % (≤ 5 %).  

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](docs/qc_severity_road_v1.0.md).
