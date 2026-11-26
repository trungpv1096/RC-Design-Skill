# Đài cọc đơn – TCVN 10304:2025 + TCVN 5574:2018 bản v3 (trang in)

Phạm vi đã thống nhất (tab Đài cọc của ETABS Tool, 2026-11-26): **đài đơn 1 cột chữ nhật, cọc BTCT ly tâm (PHC)**,
sức chịu tải cọc do người dùng nhập, tải lấy từ ETABS **Joint Reactions** (tổ hợp tính toán). TCVN 10304:2025 là bản scan,
**trang in = trang PDF**. Đài nhiều cột, sức chịu tải theo đất, liên kết cứng cọc–đài: **chưa thống nhất** – hỏi lại.

## 1. Tải và phản lực cọc (TCVN 10304:2025)
- Phản lực ETABS là lực gối tác dụng lên kết cấu → tải truyền xuống đài **ngược dấu**.
- Tải tại đáy đài: Nd,f = N + γf·G (G: đài + đất trên đài); Mx, My = mô men chân cột + V·Δz + N·(độ lệch tâm cột so
  với trọng tâm nhóm cọc). Δz = chiều cao đài H + "chân cột ETABS so với mặt đài" (0 bằng, + cao hơn, − thấp hơn).
- (3), 7.1.6.2 tr.27: Nd = Nd,f/n ± Mx·y/Σyi² ± My·x/Σxi² (+ γf·Wp trọng lượng cọc, 7.1.6.1 CHÚ THÍCH 2 tr.27).
- Trọng lượng cọc: w = γ·A, A vành khuyên theo D và chiều dày thành t (t = 0 → cọc đặc), γ = 2,5 T/m³ = 25 kN/m³;
  Wp = w·L. Ví dụ D400, t = 80 mm: A = π/4·(0,40² − 0,24²) = 0,0804 m² → w = 2,011 kN/m; L = 20 m → Wp = 40,2 kN.
- (2), 7.1.6.1 tr.26: γn·Nd ≤ Rd = Rk/γk; γn = 1,0 / 1,15 / 1,20 (cấp C1 / C2 / C3).
- 7.1.6.1 CHÚ THÍCH 3 tr.27: tổ hợp **có gió / cầu trục** → cọc biên Rd × 1,2; cọc giữa và tổ hợp không gió → Rd.
- Tổ hợp: dùng **tổ hợp thành phần** (vd. U1–U25), không dùng tổ hợp bao (Envelope) – các thành phần không đồng thời,
  không được tăng 20 %. Tổ hợp có gió nhận theo load pattern loại Wind. Đài: lấy bất lợi nhất trên mọi tổ hợp.
- Thuyết minh: bảng Nd,max / Nd,min theo tổ hợp, cột tiêu đề "Rd / 1,2Rd (kN)" chỉ ghi **một số**; tên tổ hợp bỏ
  StepType "Single Value".

## 2. Chọc thủng (TCVN 5574:2018 8.1.6, tr.83–92)
- Đường bao tính toán cách mép cột / cọc h0/2 (8.1.6.1, Hình 15); (123)–(125) tr.86 lực tập trung; (129)–(131) tr.90
  có mô men; (134)–(135) tr.91–92 đường bao hở.
- **Cột chọc thủng**: F = N − Σ phản lực các cọc nằm **trọn** trong đáy tháp (cột mở rộng h0 mỗi phía);
  M = 0,5·M chân cột (8.1.6.1) + F·độ lệch tâm so với trọng tâm đường bao.
- **Cọc chọc thủng** góc / biên đài: đường bao hở khi gần mép.
- Đường bao hở (**suy luận**, người dùng đã duyệt): khoảng cách tới mép g < h0/2 → bắt buộc hở; h0/2 ≤ g < h0 → xét cả
  kín và hở, lấy bất lợi; g ≥ h0 → chỉ kín.
- Cọc tròn quy đổi vuông cạnh 0,886D (ghi "giả định" trong thuyết minh).

## 3. Cắt và uốn
- Cắt: (88) 8.1.3.2 tr.70 dải nghiêng; (89)–(90) 8.1.3.3.1 tr.71 với Qsw = 0 (đài không đặt cốt ngang).
- Uốn: mô men tại mặt cột do phản lực cọc phía ngoài; As theo (31)–(35) tr.56–57 (αm–ξR như `san.md`), b = cạnh đài.
- Cấu tạo: 10.3.3.1 μ ≥ 0,1 % (cả thép lớp trên), 10.3.3.3 khoảng cách thanh.

## 4. Cấu tạo đài, cọc (TCVN 10304:2025)
- 8.8 tr.77: liên kết **khớp** – cọc cắm vào đài 5–10 cm; cọc chịu nhổ cần liên kết cứng (8.8 e) → tool báo
  **không đạt cấu tạo** (chưa hỗ trợ liên kết cứng).
- 8.13 tr.78: khoảng cách trục cọc ma sát ≥ 3d, cọc chống ≥ 1,5d.
- 8.3 tr.76–77: bê tông đài ≥ B15, lót ≥ B7,5, thép CB400-V / CB500-V – chỉ "về nguyên tắc", **không** đánh giá đạt / không
  trong thuyết minh (người dùng chốt).
- Hình học: tâm cọc → mép đài = e; đài không đối xứng (vd. 3 cọc): làm tròn **vị trí cột** cách mép đài bội số 50 mm gần
  trọng tâm nhóm cọc.

## 5. Thuyết minh (mẫu đã duyệt)
Không ghi: đánh giá mác bê tông / thép theo 8.3, lớp bảo vệ Bảng 19, khoảng cách cột → mép đài, đoạn giả định về đường
bao / tháp chọc thủng. Nhóm đài = cùng loại đài; cột trong nhóm được khác kích thước, mỗi cột tính với bx × by riêng.
