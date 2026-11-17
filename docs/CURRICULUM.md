# Giáo trình Quant cho AI Engineer (12 tuần)

Nguyên tắc: bạn đã biết ML/Python, nên **không** học lại code. Học phần khó và khác ML: dữ liệu tài chính nhiễu, phi dừng, dễ overfit, và chi phí giao dịch ăn hết lợi nhuận.

Chạy: `uv run jupyter lab` (notebook đặt trong `notebooks/`, code tái dùng trong `src/quant/`).

## Giai đoạn 1 — Nền tảng (tuần 1-3)
**Tuần 1: Dữ liệu & lợi suất**
- Giá, return đơn giản vs log return, điều chỉnh split/dividend, survivorship bias.
- Lab: tải dữ liệu bằng `yfinance`, tính return, vẽ phân phối. Quan sát fat tails (kurtosis), so với Gaussian.

**Tuần 2: Rủi ro & chỉ số hiệu suất**
- Volatility, drawdown, Sharpe, Sortino, Calmar, VaR/CVaR.
- Lab: viết hàm `metrics(returns)` trong `src/quant/metrics.py` kèm vài assert.

**Tuần 3: Thống kê chuỗi thời gian**
- Stationarity (ADF), autocorrelation, heteroskedasticity (GARCH cơ bản), cointegration.
- Lab: kiểm định giá vs return có dừng không; vẽ ACF của return và return².

## Giai đoạn 2 — Chiến lược & backtest (tuần 4-6)
**Tuần 4: Backtest vectorized**
- Signal -> position -> PnL, **shift(1) để tránh look-ahead**, phí & slippage.
- Lab: momentum và mean-reversion đơn giản trên 1 mã.

**Tuần 5: Cạm bẫy backtest** (tuần quan trọng nhất)
- Overfitting, data snooping, multiple testing, walk-forward, purged/embargoed CV, Deflated Sharpe.
- Lab: tạo 1000 chiến lược ngẫu nhiên, chọn cái tốt nhất, thấy "alpha" giả.

**Tuần 6: Factor investing**
- CAPM, Fama-French, momentum/value/quality/low-vol, cross-sectional ranking.
- Lab: xếp hạng rổ cổ phiếu theo momentum 12-1, long-short theo decile.

## Giai đoạn 3 — Danh mục & thực thi (tuần 7-9)
**Tuần 7: Portfolio construction**
- Markowitz, shrinkage covariance (Ledoit-Wolf), risk parity, Kelly.
- Lab: so sánh equal-weight, min-variance, risk-parity out-of-sample.

**Tuần 8: Quản trị rủi ro & sizing**
- Vol targeting, stop-loss có thật sự giúp?, exposure/leverage, tail risk.

**Tuần 9: Chi phí & vi cấu trúc thị trường**
- Spread, market impact, turnover, capacity, order book cơ bản.
- Lab: sweep phí để thấy chiến lược nào sống sót.

## Giai đoạn 4 — ML cho quant (tuần 10-12)
**Tuần 10: Feature & label cho tài chính**
- Triple-barrier labeling, meta-labeling, fractional differentiation, sample weighting (theo López de Prado).

**Tuần 11: Mô hình**
- Gradient boosting trước, deep learning sau. Đánh giá bằng IC (information coefficient) và PnL sau phí, không phải accuracy.

**Tuần 12: Capstone**
- Một chiến lược đầy đủ: dữ liệu -> feature -> walk-forward -> chi phí -> báo cáo rủi ro. Phải có phần "vì sao nó có thể thất bại".

## Sách / nguồn
1. *Quantitative Trading* — Ernest Chan (nhập môn thực dụng)
2. *Advances in Financial Machine Learning* — López de Prado (ML + backtest đúng cách)
3. *Systematic Trading* — Robert Carver (sizing, thực tế)
4. *Active Portfolio Management* — Grinold & Kahn (khung alpha/IC)
5. *Options, Futures and Other Derivatives* — Hull (khi cần phái sinh)

## Quy tắc vàng
- Mặc định bạn **không có alpha**; backtest đẹp thường là bug hoặc overfit.
- Luôn trừ phí. Luôn out-of-sample. Luôn shift tín hiệu.
- Chưa dùng tiền thật cho tới khi paper-trade ít nhất 3 tháng.
