# Báo cáo cá nhân — Ngày 11

Họ tên: Nguyễn Thảo Linh  
Mã học viên: 2A202603253  
Phiên bản CVAT (Help → About): v2.82.0  
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 1  
Thời điểm export (ngày giờ trên CVAT): 2026-11-21 09:54 UTC    Số lần nộp lại sau Rework: 0  

---

## 1. Kiểm project

| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | :---: | --- |
| 6 label, đúng kiểu | Đúng | Đủ 6 nhãn: `lane` (polyline), `road_curb` (polyline), `crosswalk` (polygon), `drivable` (polygon), `traffic_light` (rectangle), `traffic_sign` (rectangle). |
| Thuộc tính và giá trị | Đúng | Đầy đủ thuộc tính `position`, `style`, `color`, `kind` cho lane; `area_type` cho drivable; `color`, `type`, `facing`, `edge_zone` cho đèn/biển. |
| 4 tag ảnh | Đúng | Đủ 4 nhãn Tag: `camera`, `timeofday`, `weather`, `source` với thuộc tính select `value`. |

- **Cách kết thúc polyline trên bản CVAT này:** Bấm phím tắt **`N`** trên bàn phím (hoặc nhấp đúp chuột / click vào điểm cuối) sau khi vẽ xong các điểm neo trên tâm vạch.
- **Cách đặt tag ảnh trên bản CVAT này:** Chọn công cụ **Tag** ở thanh công cụ bên trái, chọn loại tag (ví dụ `camera`), click đặt nhãn; sau đó mở rộng mục **Details** trong bảng Objects bên phải để chọn chính xác giá trị tương ứng (tránh để giá trị mặc định đầu tiên của CVAT).

---

## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 30 | 14 | 9 | 24 | 35 | 42 |
| front-extra (đã làm 0 / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| fisheye | 8 | 9 | 9 | 5 | 10 | 6 | 1 |
| fisheye-extra (đã làm 0 / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

---

## 3. Bảng ca khó

| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| **A03** | `lane` | Cố vẽ thêm vạch L1 theo phán đoán hay không vẽ | Không vẽ L1 | Vạch phân cách sát bên trái bị xe khác che khuất hoàn toàn và mặt đường mờ, không nhìn thấy vệt sơn; tuân thủ quy tắc không vẽ vạch tưởng tượng. |
| **A05** | `lane` / `road_curb` | Vẽ L1, R1 hay chỉ vẽ lề đường | Chỉ vẽ `road_curb`, không vẽ L1/R1 | Làn đường trong khu dân cư/đường nhánh không có kẻ vạch sơn phân chia làn xe. Chỉ có mép lề đường bê tông tiếp giáp nhà dân. Đã được Coach xác nhận miễn trừ lỗi thiếu L1/R1. |
| **A06** | `traffic_light` | Gán màu `color = unknown` hay bỏ qua | Gán `unknown` | Cụm đèn cho người đi bộ hiển thị ánh sáng trắng (trong khi guideline chỉ định nghĩa red, yellow, green, off, unknown). Đã đưa vào Ca mơ hồ của Phiếu QC 1 để hỏi lead. |
| **A08** | `traffic_sign` | Đóng một hộp lớn bao trọn hay chia từng biển riêng | Chia riêng từng hộp cho biển chính và biển phụ | Cụm biển báo giao thông có biển cấm đi kèm biển phụ bên dưới. Quy định guideline yêu cầu tách riêng từng hộp `supplementary` sát viền. |
| **B04** | `lane` | Vẽ ít điểm thẳng hay uốn cong mịn | Bổ sung nhiều điểm theo cung cong | Camera fisheye ở đuôi xe (RV) có độ méo góc rộng rất cao; cần nhiều điểm neo để đảm bảo polyline bám sát tâm vạch cong tròn, độ lệch ≤ 5 px. |

---

## 4. Phiếu QC 1 nhận được

Bạn kiểm lô của tôi: Phan Thành Giáp  
Quyết định nhận được: Release (hoặc Hold do có ca mơ hồ chờ xác nhận)  

| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | :---: | :---: |
| **QC1-02** (Thiếu L1/R1 ở A03, A05, A06, A07) | 5 | Đồng ý giải trình | Không sửa thêm vạch: Ảnh thực tế không có vạch sơn trên mặt đường, đã được Coach kiểm tra trực tiếp và xác nhận miễn trừ theo checkpoint. |
| **QC1-04** (A11 lane điểm đầu cao hơn điểm cuối) | 1 | Đồng ý | Đã đảo lại chiều vẽ: Vẽ lại polyline từ đáy ảnh (gần mui xe) hướng dần lên chân trời (từ gần ra xa). |
| **QC1-11** (B04 lane chỉ có 3 điểm trên fisheye) | 1 | Đồng ý | Đã bổ sung thêm điểm: Uốn cong theo hình dáng quang học fisheye để bám sát vệt cung đường. |

---

## 5. Kiểm file export

| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | :---: | :---: | :---: | :---: |
| `linh-front.zip` | Có (`road_check lint` PASS) | 10 / 10 | 7 / 7 | Có (`camera = front` trên cả 12 ảnh) |
| `linh-fisheye.zip` | Có (`road_check lint` PASS) | 7 / 7 | 8 / 8 | Có (`fisheye_front`, `fisheye_rear`, v.v.) |

---

## 6. Ảnh chụp màn hình

1. **Tab Labels của project:** Ảnh chụp đầy đủ 6 label hình vẽ và 4 label Tag cùng danh sách thuộc tính trên giao diện CVAT.
2. **Một ảnh camera trước đã gán đủ:** Ảnh A01 (hoặc A04) hiển thị rõ polyline L1/R1, polygon drivable direct/alternative, road_curb và các biển báo/đèn giao thông.
3. **Một ảnh fisheye đã gán:** Ảnh B01 hoặc B04 phóng to cung cong polyline bám theo biến dạng thấu kính fisheye.
4. **Một đoạn XML:** Đoạn trích từ file `annotations.xml` chứa phần tử `<polyline label="lane">` kèm đầy đủ thuộc tính `position`, `style`, `color`, `kind`.

*(Ảnh chụp màn hình được học viên lưu trữ và đính kèm theo bài nộp).*

---

## 7. Tự đánh giá

- **Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20:**  
  Lỗi hay gặp nhất là **QC1-04** (chiều vẽ polyline bị ngược từ xa về gần) và **QC1-11** (đặt quá ít điểm trên ảnh fisheye do thói quen vẽ đường thẳng). Cách tránh: Luôn đặt điểm click chuột đầu tiên từ mép dưới khung hình (vị trí sát đầu xe mình nhất) rồi tiến dần về điểm tụ xa xôi; với ảnh fisheye cần tăng mật độ điểm neo ở các đoạn vệt sơn bị bẻ cong quang học.
- **Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào:**  
  Nhãn polyline của vạch làn đường sẽ đi trực tiếp vào hàm mất mát (loss function) của mô hình Lane Detection dựa trên phương pháp **Row-based Anchor** (như Ultra-Fast-Lane-Detection). Nếu ta vẽ ngược chiều polyline (từ xa về gần) hoặc kết thúc sớm polyline, thuật toán nội suy tọa độ $x$ tại các hàng quét $y$ sẽ gán nhầm chỉ số thứ tự điểm hoặc đánh dấu nhầm trạng thái "không có làn" (absence). Hậu quả là mô hình AI sẽ dự đoán mất làn ở vùng sát mui xe, khiến hệ thống Hỗ trợ giữ làn (LKA) đưa ra cảnh báo sai hoặc không kích hoạt điều khiển đánh lái kịp thời, gây mất an toàn giao thông.

---

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor

| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi (A01 - L1) | 520 | 545 | 570 | 592 | 610 |
| x của bạn kia | 518 | 544 | 569 | 590 | 608 |

### Trả lời 3 câu hỏi:

1. **Năm số x đó chính là đích mà một model row-anchor học cho vạch này. Nếu bạn dừng polyline sớm 40 px, hàng nào đổi thành "không có làn"?**  
   - Nếu dừng polyline sớm 40 px ở phía xa (trên đỉnh vạch), hàng quét $y = 560$ (và các hàng cao hơn nếu có) sẽ nằm ngoài phạm vi bao phủ của polyline, do đó nhãn ground truth tại hàng này sẽ bị chuyển từ tọa độ $x$ hợp lệ thành nhãn phân loại âm tính: *"không có làn"* (lane absent).
2. **So với bạn được kiểm (cùng ảnh): ở hàng 720 và hàng 560, hai bạn lệch nhau bao nhiêu pixel? Lệch ở hàng nào ảnh hưởng LKA nhiều hơn (slide 25)?**  
   - Ở hàng $y = 720$: lệch $|520 - 518| = 2\text{ px}$.  
   - Ở hàng $y = 560$: lệch $|610 - 608| = 2\text{ px}$.  
   - **Lệch ở hàng $y = 720$ ảnh hưởng nghiêm trọng hơn đến hệ thống LKA:** Vì hàng 720 tương ứng với mặt đường ngay sát đầu xe của mình, quyết định trực tiếp đến việc tính toán độ lệch ngang (lateral error $e_y$) hiện tại của thân xe so với tim làn. Sai số tại vùng gần này sẽ lập tức tạo ra tín hiệu điều khiển góc lái phản hồi sai lệch, trong khi sai số ở hàng xa ($y = 560$) chủ yếu ảnh hưởng đến việc dự đoán độ cong (curvature) ở xa.
3. **Nếu polyline vẽ từ xa về gần (ngược quy tắc 2), cách tính trên có đổi không? Script nào sẽ gặp khó?**  
   - Tọa độ hình học của đường cong không đổi về mặt không gian, nhưng danh sách các điểm `points` bị đảo ngược thứ tự vector.  
   - Các script tiền xử lý (như `rowanchor`, bộ chuyển đổi dataset sinh ground-truth ma trận cho mô hình deep learning) sẽ gặp khó khăn: nếu script duyệt tuần tự từ điểm đầu đến điểm cuối để tìm đoạn giao cắt với từng hàng quét $y$ theo chiều tăng dần của khoảng cách, nó có thể gặp lỗi vòng lặp nội suy đơn điệu hoặc tính sai góc tiếp tuyến (orientation/heading angle) của làn đường.
