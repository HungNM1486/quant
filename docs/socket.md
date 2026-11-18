## Socket.IO

* **Địa chỉ:** `wss://vcbsprice.vcbs.com.vn`, namespace `/ps`, Socket.IO client v2.
* **Đăng ký:** gửi event `regs` với payload `{"action":"join","data":"{sym},{sym}_LS,{sym}_NTP,{sym}_TP"}`.
* **Giữ kết nối:** cứ 10 giây gửi event `regs` với payload `{"action":"ping","mode":"sync","data":" "}`.
* **Nhận:** event `public`, dạng `{"data": {...}}`. App xử lý các loại tin theo `data.id`:

| id | Nội dung | Dùng để |
| :--- | :--- | :--- |
| 3220 | Khớp lệnh | Dựng tick: giá, khối lượng, khối lượng lũy kế. |
| 3211 | Sổ lệnh 10 mức | Sổ lệnh thời gian thực. |
| 3210 | Quote, 3 mức giá và tóm tắt sổ lệnh | Sổ lệnh dự phòng khi chưa có 10 mức. |
| 3250 | Khối ngoại | Không lưu (collector bỏ qua). Khối ngoại trên bảng giá web lấy từ snapshot HTTP. |
| 1151 | Trạng thái thị trường | Trạng thái phiên (`market_status`). |  