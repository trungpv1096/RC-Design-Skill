---
name: rc-design-tcvn
description: Tính toán / kiểm tra cấu kiện bê tông cốt thép CỘT, DẦM, SÀN, ĐÀI CỌC theo TCVN 5574:2018 (bản v3), TCVN 10304:2025 và cột kháng chấn theo TCVN 9386-1:2025 – vật liệu, uốn (dải 1 m, tiết diện chữ nhật), nén lệch tâm / uốn xiên (mô hình phi tuyến 8.1.2.7, η, ea), cắt (8.1.3, φn), xoắn (8.1.4), chọc thủng (8.1.6), cấu tạo (10.2, 10.3), phản lực cọc, vùng tới hạn / bó lõi / lực cắt theo khả năng, cột khỏe – dầm yếu (4.29). Dùng khi người dùng nhờ "tính thép cột / dầm / sàn", "kiểm tra đài cọc / sức chịu tải cọc", "kiểm tra cột theo TCVN", "giải thích kết quả ETABS Concrete Frame Design TCVN", "kiểm tra cấu tạo kháng chấn cột", "cột khỏe dầm yếu", hoặc đối chiếu thuyết minh của ETABS Tool (D:\Tools\etabs_tool) với tiêu chuẩn. Không dùng cho kết cấu thép (xem skill etabs-model-steel-structure).
---

# Thiết kế cột / dầm / sàn BTCT theo TCVN

Skill tổng hợp phương pháp đã thống nhất với người dùng khi xây dựng ETABS Tool (tab Cột TCVN, Thép dầm, Thép sàn,
Kiểm tra cột kháng chấn). Mọi công thức đã đối chiếu ảnh trang tiêu chuẩn; chỗ nào là **suy luận** đều ghi rõ.

## Nguồn tiêu chuẩn (đọc trước khi trích dẫn)
| Tài liệu | File | Ghi chú đọc |
|---|---|---|
| TCVN 5574:2018 **bản v3** (chuẩn trích dẫn) | `V:\02. Quy Định Nhà Nước QCVN- TCVN\02. Standard & Design Documents\01. QCVN-TCVN-Nghị định\03. TCVN - BTCT\TCVN 5574_2018 v3.pdf` (bản scan; bản text `TCVN 5574-2018.pdf` cùng thư mục) | **Trang in = trang PDF + 2**. Công thức phải đọc từ ảnh trang (render PNG bằng pypdfium2 trong `%USERPROFILE%\Tools\markitdown-env`), text MarkItDown làm vỡ công thức |
| TCVN 9386-1:2025 (động đất) | `V:\02. Quy Định Nhà Nước QCVN- TCVN\TCVN gui Skill AI\Thiết kế Kết cấu\Động đất\TCVN9386-1_2025_922314.pdf` | Bản scan, **trang in = trang PDF + 4** (phần thân) |
| TCVN 10304:2025 (móng cọc) | do người dùng cung cấp | Bản scan, **trang in = trang PDF** |
| TCVN 2737:2023 (tải trọng, tổ hợp) | `V:\02. Quy Định Nhà Nước QCVN- TCVN\02. Standard & Design Documents\01. QCVN-TCVN-Nghị định\11. TCVN- TAI TRONG\TCVN 2737-2023 Tai trong va tac dong - final.pdf` | Có text; tải dài hạn 5.4h, 8.3.3 (0,35·qk) |
| ETABS CFD-TCVN-5574-2018 (manual CSI) | do người dùng cung cấp | Cách ETABS tính cột: xem `cot.md` mục "So với ETABS" |

Không có file / không đọc được trang → nói rõ, **không trích số từ trí nhớ**.

## Quy trình chung
1. **Xác định dữ liệu**: cấp bê tông, nhóm thép (dọc, đai), kích thước, lớp bảo vệ, nội lực + tổ hợp (tổ hợp nào là
   dài hạn), điều kiện làm việc (Bảng 19), cách đổ bê tông (γb3). Thiếu → hỏi, không giả định ngầm.
2. **Vật liệu**: theo `vat-lieu.md` (Rb, Rbt, Eb, Rs, Rsc, Rsw, γb1, γb3).
3. **Tính theo loại cấu kiện**:
   - Cột: `cot.md` (η, ea, phi tuyến 8.1.2.7, cắt có φn, cấu tạo 10.2–10.3).
   - Dầm: `dam.md` (uốn, cắt, xoắn 8.1.4; tổng hợp kết quả ETABS Concrete Frame Design).
   - Sàn: `san.md` (dải 1 m từ Strip Forces, αm–ξR, cấu tạo bản).
   - Cột kháng chấn, cột khỏe – dầm yếu (4.29): `khang-chan.md` (TCVN 9386-1:2025).
   - Đài cọc đơn: `dai-coc.md` (phản lực cọc TCVN 10304:2025, chọc thủng / cắt / uốn đài TCVN 5574:2018).
4. **Trình bày**: công thức → thay số → kết quả có đơn vị; ghi điều / công thức / trang in; hệ số sử dụng k ≤ 1 → Đạt.
5. Trả lời chat kết thúc bằng: "Kết quả chỉ mang tính tham khảo; người ký duyệt cần kiểm tra lại trước khi sử dụng."
   **Không** đưa câu này, và các cảnh báo phần mềm, vào thuyết minh / file do tool xuất ra.

## Quy ước bắt buộc
- Đơn vị: nội lực kN, kN·m; tiết diện mm; cường độ MPa; As cm² (dầm, cột) hoặc cm²/m (sàn, đai Asw/s).
- Quy ước trục ETABS: t3 = chiều cao (song song trục 2), t2 = bề rộng; V2 đi với M3, V3 đi với M2. P < 0 là nén.
- Lớp bảo vệ `cover` tính **đến mép ngoài cốt đai** (như ETABS): thép dọc có lớp bảo vệ c = cover + Øđai;
  a = cover + Øđai + d/2.
- Dẫn chiếu TCVN 5574:2018 theo **bản v3** (người dùng chốt 2026-11-18).
- Phân biệt rõ: nội dung tiêu chuẩn / cách ETABS làm / cách ETABS Tool làm / **suy luận** của Claude.

## Liên hệ ETABS Tool
Code tham chiếu (đọc khi cần chi tiết, không sửa nếu chưa được yêu cầu): `D:\Tools\etabs_tool\etabs_tool\core\`
`tcvn_mat.py`, `col_section.py`, `col_check.py`, `col_seismic.py`, `scwb.py` (4.29), `cap_check.py` (đài cọc),
`beam_design.py`, `slab_strip.py`. Vòng lặp đọc / tính / xuất dài gọi `progress.tick()` (hộp tiến độ có nút Dừng).
Tool chạy bằng `run.bat` (pythonw); trước khi mở lại phải kiểm tra không còn tiến trình `*main.py*`.
