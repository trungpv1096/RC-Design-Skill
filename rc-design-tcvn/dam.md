# Dầm BTCT – TCVN 5574:2018 bản v3 (trang in)

Thực tế dự án: As yêu cầu của dầm lấy từ **ETABS Concrete Frame Design (TCVN 5574-2018)**; việc của kỹ sư / tool là
tổng hợp theo vùng, bố trí thép và kiểm tra Fs. Khi cần tính tay hoặc kiểm lại ETABS, dùng các công thức dưới.

## 1. Tổng hợp kết quả ETABS (cách tab Thép dầm của ETABS Tool làm)
- Đọc `DesignConcrete.GetSummaryResultsBeam` (kN-m-C → cm², cm²/m).
- Gom nhịp thành dầm liên tục theo UniqueName dạng `<Tên dầm>-<số nhịp>` (vd. RB2-1, RB2-2).
- Mỗi nhịp 3 vùng: **Gối trái / Giữa nhịp / Gối phải**; vùng gối = k·L (mặc định k = 0,25). Lấy As max trên & dưới
  từng vùng; Asw/s max vùng gối và vùng giữa.
- Gối chung của 2 nhịp liền kề: lấy giá trị lớn hơn.
- Có xoắn: dùng giá trị **tổng có xoắn** của ETABS (AsTopTotal, AsBotTotal, AtTrnTotal – bảng
  "Concrete Beam Design Summary").
- Thép bố trí: chuỗi `2d18+1d16` (thép dọc), `d8a150` (2 nhánh) / `4d8a150` (4 nhánh) cho đai → Asw/s = n·πd²/4/s.
  Thép dọc = thép chạy suốt cả dầm + gia cường tại vùng. **Fs = As bố trí / As yêu cầu** (As yc = 0 → "CT" cấu tạo).
- μ = As/(b·h) × 100 %.

## 2. Uốn – tiết diện chữ nhật, cốt đơn (8.1.2.3, (33)–(35), tr.57)
- αm = M/(Rb·b·h0²); αm ≤ αR (xem ξR trong `vat-lieu.md`), nếu αm > αR → tăng tiết diện / mác bê tông (hoặc đặt cốt kép
  – chưa thống nhất cách tính trong skill, tra lại 8.1.2.3 trước khi dùng).
- ξ = 1 − √(1 − 2αm); As = ξ·Rb·b·h0/Rs.
- Kiểm tra: x = Rs·As/(Rb·b) ≤ ξR·h0; Mu = Rb·b·x·(h0 − 0,5x) ≥ M.
- Tiết diện chữ T (cánh sàn) **chưa thống nhất** – đọc 8.1.2.3 trên ảnh trang trước khi tính.

## 3. Cắt (8.1.3, tr.70–73)
Cùng hệ công thức với cột (`cot.md` mục 5): (88) dải nghiêng, (93)–(95) Qb,1 + Qsw,1, (96) điều kiện kể đai,
(98) sw,max. Dầm thông thường N ≈ 0 → φn = 1 (8.1.3.3.2). Cách tính đầy đủ theo tiết diện nghiêng (89)–(91) dò C trong
[h0; 2h0] khi cần chính xác hơn.

## 4. Xoắn (8.1.4, từ tr.75)
- (102), 8.1.4.2.1: T ≤ 0,1·Rb·b²·h (b cạnh nhỏ, h cạnh lớn) – không đạt thì phải **tăng tiết diện**, tăng thép không giải
  quyết được.
- (103), 8.1.4.2.2: T ≤ Tsw + Ts (đai + thép dọc). Tỷ số (qsw,1·Z1)/(Rs·As,1) lấy trong **0,5 – 1,5** (ETABS mục 07 = 1).
- Xoắn + uốn: 8.1.4.3; xoắn + cắt: 8.1.4.4 (đọc ảnh trang khi cần công thức).
- **Thực hành (suy luận, TCVN không nêu)**: xoắn tương thích ở dầm biên do sàn / dầm phụ gác vào thường bị mô hình đàn
  hồi phóng đại → giảm Torsion Constant modifier (vd. 0,01–0,1) nhưng vẫn để Torsion = Yes để xoắn cân bằng (ô văng,
  sê nô) vẫn được tính. Mức giảm do chủ trì quyết định, ghi vào thuyết minh.

## 5. Cấu tạo (đã đối chiếu)
- 10.3.3.1: μ = As/(b·h0) ≥ 0,1 % (cấu kiện chịu uốn).
- 10.3.4.3: khi cần đai chịu cắt, bước đai ≤ min(0,5h0; 300 mm).
- Lớp bảo vệ: Bảng 19 (như cột). Các yêu cầu khác của 10.3 cho dầm (khoảng cách thanh, neo, cắt thép, đai cấu tạo…)
  **chưa tổng hợp** – tra 10.3 trên ảnh trang trước khi kết luận.
