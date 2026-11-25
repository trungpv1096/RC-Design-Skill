# Sàn BTCT theo dải (strip) – TCVN 5574:2018 bản v3 (trang in)

ETABS 23 không có TCVN cho Slab Design → lấy mô men từ **Strip Forces** rồi tự tính As theo TCVN (cách tab Thép sàn của
ETABS Tool, đã chốt với người dùng 2026-11-19).

## 1. Nội lực
- Bảng ETABS: `Strip Object Connectivity` (strip, tầng, layer, bề rộng), `Strip Forces` (M3 theo trạm, CutWidth – cần
  chạy phân tích), `Concrete Slab Design Summary - Span Definition Data` (SpanID, StartDist, SpanLength – cần chạy Slab
  Design) hoặc nhịp suy từ giao strip với dầm / cột / tường.
- Quy đổi về dải 1 m: m = M3 / CutWidth (kN·m/m).
- Dấu: M3 < 0 → căng thớ trên (thép trên); M3 > 0 → căng thớ dưới.
- Vùng: Gối trái / Giữa nhịp / Gối phải, vùng gối = k·L (mặc định 0,25); gối chung 2 nhịp lấy max; nhóm strip lấy max
  theo vị trí.

## 2. As yêu cầu (8.1.2.2.3 (31)–(32) tr.56; 8.1.2.3 (33)–(35) tr.57), b = 1000 mm
- h0 = h − a (a: mép → trọng tâm thép, nhập riêng thép trên / dưới).
- αm = m·10⁶/(Rb·1000·h0²); αR = ξR(1 − 0,5ξR), ξR = 0,8/(1 + Rs/Es/0,0035).
- αm > αR → KHÔNG tính được, tăng chiều dày sàn / mác bê tông.
- ξ = 1 − √(1 − 2αm); As = ξ·Rb·1000·h0/Rs (mm²/m) → /100 = cm²/m.
- Rb nhân γb1 theo tổ hợp (6.1.2.3a).

## 3. Kiểm tra thép bố trí
- Chuỗi `d10a200` hoặc `d10a200+d12a400` (thép chạy suốt + gia cường; có thể khác nhóm thép – d < 10 nhóm nhỏ, d ≥ 10
  nhóm lớn).
- As = Σ πd²/4·1000/s; x = ΣRs·As/(Rb·1000); ξ = x/h0, nếu ξ > ξR lấy x = ξR·h0 (**suy luận**: phần thép vượt không kể);
  Mu = ΣRs·As·(h0 − 0,5x) ≥ m.
- ξR khi trộn nhóm thép: lấy ξR nhỏ nhất (thép bền hơn).

## 4. Cấu tạo bản
| Điều | Yêu cầu |
|---|---|
| 10.3.3.1 (tr.135) | μs = As/(b·h0) ≥ 0,1 % → As,min = 0,001·1000·h0 |
| 10.3.3.3 (tr.136) | Khoảng cách thép ≤ 200 mm khi h ≤ 150 mm; ≤ min(1,5h; 400) mm khi h > 150 mm. Lớp gộp chạy suốt + gia cường: khoảng cách = bước nhỏ nhất (vd. d10a200 + d10a400 → 200) |
| 10.3.3.5 (tr.136) | Thép dưới kéo vào gối ≥ 1/3 thép dưới giữa nhịp (trên 1 m bề rộng) |

## 5. Kết luận theo nhóm strip
Đạt khi mọi vùng Mu ≥ m, đủ As,min, khoảng cách đạt, neo 10.3.3.5 đạt; báo Fs nhỏ nhất. Vùng m = 0 → bố trí cấu tạo.
