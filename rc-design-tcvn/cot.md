# Cột BTCT chữ nhật – TCVN 5574:2018 bản v3 (trang in)

Trình tự cho mỗi tổ hợp và mỗi vị trí (station): ea → e0 → η → M* = η·e0·N theo từng phương → kiểm tra N–M uốn xiên
→ cắt hai phương → cấu tạo cho cả nhóm cột.

## 1. Chiều dài tính toán L0 (8.1.2.4.4, tr.62) – L0 = ψ·L
| Sơ đồ liên kết 2 đầu | ψ |
|---|---|
| Hai đầu khớp | 1,0 |
| Ngàm cứng – tự do (công xôn) | 2,0 |
| Khớp cố định – ngàm cứng | 0,7 |
| Khớp cố định – ngàm nửa cứng | 0,9 |
| Khớp di động hạn chế – ngàm cứng | 1,5 |
| Khớp di động hạn chế – ngàm nửa cứng | 2,0 |
| Hai đầu ngàm | 0,5 |
| Hai đầu ngàm nửa cứng | 0,8 |
| Hai đầu ngàm di động hạn chế (ngàm cứng) | 0,8 |
| Hai đầu ngàm di động hạn chế (ngàm nửa cứng) | 1,2 |
L = chiều cao cột thực tế (nếu phần tử ETABS bị chia đoạn phải nhập L thật). Mặc định người dùng: ψ nhập theo từng cột.

## 2. Độ lệch tâm (8.1.2.2.4, tr.56–57)
- ea ≥ max(L/600; h/30; 10 mm).
- Kết cấu **siêu tĩnh** (khung thông thường): e0 = max(e tĩnh học; ea). **Tĩnh định**: e0 = e tĩnh học + ea.
- e tĩnh học = |M|/N. Cấu kiện chịu kéo: không xét ea, η.

## 3. Uốn dọc – hệ số η ((44)–(48), 8.1.2.4.2; người dùng chốt dùng η, không dùng P-Delta)
- Bỏ qua η (η = 1) khi L0/i ≤ 14 (8.1.2.1.2), i = √(I/A).
- η = 1/(1 − N/Ncr); Ncr = π²·D/L0²; D = kb·Eb·I + ks·Es·Is; ks = 0,7.
- kb = 0,15 / [φL·(0,3 + δe)]; δe = e0/h, giới hạn 0,15 ≤ δe ≤ 1,5.
- φL = 1 + ML1/ML ≤ 2; ML = |M| + N·zs, ML1 = M_l + N_l·zs (nội lực tổ hợp **dài hạn** cùng vị trí; zs = khoảng cách
  trọng tâm tiết diện → thanh biên xa nhất theo phương uốn). Không có tổ hợp dài hạn → φL = 2 (bất lợi).
- N ≥ Ncr → mất ổn định, KHÔNG ĐẠT.
- Tính riêng cho M3 (h = t3) và M2 (h = t2), mỗi phương có L0 riêng.

## 4. Độ bền tiết diện thẳng góc – mô hình biến dạng phi tuyến (8.1.2.7, (59)–(63), (70), (71), (86))
- Tích phân theo thớ; bê tông 2 đoạn thẳng (εb1,red = 0,0015, εb2 = 0,0035), không kể chịu kéo; thép tại đúng vị trí
  thanh, σs = Es·εs giới hạn −Rs ≤ σs ≤ Rsc, εs,u = 0,025; khi toàn tiết diện chịu nén εb,u theo (86).
- Dựng mặt tương tác (N, M3, M2) theo góc trục trung hòa θ (72 góc).
- **Hệ số sử dụng của tool**: k = max(M/Mu; N/Nu), Mu cùng phương vectơ (M3*, M2*) **tại cùng N**.
- Tổ hợp dài hạn: mặt riêng với Rb·0,9 (γb1) và Rsc ngoài ngoặc. Tổ hợp thường: Rb·1,0 và Rsc trong ngoặc.
- Kiểm tra tay (để đối chiếu): N0 = Rb·(A − As) + σs·As với σs = min(Es·εb0; Rsc); kéo đúng tâm = Rs·As.

### So với ETABS Concrete Frame Design (manual CFD-TCVN 5574-2018, 3.4.1 tr.16–19; 3.4.2.3 tr.23)
- ETABS dùng **khối ứng suất chữ nhật** Rb, chiều cao x = c·(εb2 − εb1)/εb2 = 0,571c (CSI tự suy từ biểu đồ 6.1.4.3 –
  **suy luận**), hợp lực ≈ 73 % so với biểu đồ 2 đoạn thẳng (0,786·Rb·b·c).
- Hệ số CR = OL/OC theo **tia từ gốc** trong không gian (N, M2, M3), nội suy tuyến tính 24 đường × 11 điểm → thô,
  thiên an toàn. Tăng *Number of Interaction Points* (Preferences mục 04) để kiểm.
- Ví dụ C300x300 (B25, 8Ø18, γb3 0,85): tool k = 0,557; ETABS CR = 0,68 – cả hai đạt. Vùng N lớn ETABS thấp hơn mô tả
  của manual 10–20 %, **chưa giải thích được**.
- ETABS "Fiber Model" dùng Rb,n (cường độ tiêu chuẩn), không dùng để kiểm tra thiết kế.
- Preferences: mục 05 *Minimum Eccentricity* = Yes (ea); 06 *Torsion* = Yes; 07 tỷ số thép xoắn = 1 (0,5–1,5).

## 5. Lực cắt (8.1.3, tr.70–73) – mỗi phương độc lập
| Công thức | Nội dung |
|---|---|
| (88) | Dải bê tông giữa tiết diện nghiêng: Q ≤ φn·φb1·Rb·b·h0, φb1 = 0,3 |
| (93) | Q1 ≤ Qb,1 + Qsw,1 (cách đơn giản, không dò C) |
| (94) | Qb,1 = 0,5·φn·Rbt·b·h0 |
| (92) | qsw = Rsw·Asw/sw (N/mm) |
| (95) | Qsw,1 = qsw·h0 |
| (96) | qsw ≥ 0,25·Rbt·b thì mới kể đai (không thỏa → Qsw,1 = 0, hoặc dùng (97)) |
| (98) | sw,max = Rbt·b·h0²/Q – bước đai được kể vào tính toán |
- **φn (8.1.3.3.2, tr.72–73)** nhân vào vế phải (88), (90), (94); σ = N/Ared, Ared = A + (Es/Eb − 1)·As (tool luôn kể
  thép):
  - σm ≤ 0,25Rb: φn = 1 + σm/Rb; 0,25Rb < σm ≤ 0,75Rb: φn = 1,25; 0,75Rb < σm ≤ Rb: φn = 5(1 − σm/Rb);
  - kéo σt ≤ Rbt: φn = 1 − σt/(2Rbt);
  - σm > Rb hoặc σt > Rbt: ngoài phạm vi → KHÔNG ĐẠT, đề nghị tăng tiết diện / mác bê tông.
- k cắt = max(Q/(Qb,1 + Qsw,1); Q/(88)).
- Ví dụ C300x300, V2: h0 = 258 mm, Rb = 12,33, Rbt = 1,05 MPa, σm = 3,18 MPa (> 0,25Rb = 3,08) → φn = 1,25;
  (88) = 1,25×0,3×12,33×300×258 = 357,7 kN; Qb,1 = 1,25×0,5×1,05×300×258 = 50,79 kN; Qsw,1 = 170,9×258 = 44,09 kN;
  k = 22,90/94,88 = 0,241.

## 6. Cấu tạo (10.2, 10.3; tr.133–137)
| Điều | Yêu cầu |
|---|---|
| 10.2.2 | Độ mảnh L0/i ≤ 120 (cột nhà) |
| 10.3.1, Bảng 19 | Lớp bảo vệ thép dọc ≥ 20 / 25 / 30 / 40 mm (trong nhà ẩm ≤ 75 % / > 75 % / ngoài trời / trong đất) và ≥ d |
| 10.3.2 | Khoảng hở thanh đặt đứng ≥ max(50 mm; d) |
| 10.3.3.1 | μ min mỗi phía nội suy 0,1 % (λ ≤ 17) → 0,25 % (λ ≥ 87); thép rải theo chu vi: μ toàn bộ ≥ 2×μmin |
| 10.3.3.3 | Khoảng cách trục thanh dọc ≤ 400 mm |
| 10.3.4.2 | Ø đai ≥ max(0,25·dmax; 6 mm) |
| 10.3.4.3 | Khi cần đai chịu cắt (Q > Qb,1): bước ≤ min(0,5h0; 300) |
| 10.3.4.4 | Bước đai ≤ min(15d; 500); nếu thép 1 mặt > 1,5 % → ≤ min(10d; 300) |
| 10.3.4.5 | Thanh dọc (ít nhất cách 1 thanh) nằm ở góc uốn đai, góc uốn cách ≤ 400 mm; mặt rộng ≤ 400 mm và ≤ 4 thanh → cho phép 1 đai ôm |

## 7. Trình bày thuyết minh (mẫu đã duyệt)
Thông số (vật liệu 3 dòng, hình học, L, L0, môi trường) → N–M (trường hợp bất lợi + bảng η + 5 trường hợp k lớn nhất)
→ biểu đồ tương tác (3D + mặt cắt) → cắt (bảng V2/V3) → cấu tạo → kháng chấn (nếu có) → kết luận một dòng.
