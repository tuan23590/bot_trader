# 🚀 Hệ Thống Master-Slave Trading MT5

Hệ thống copy lệnh giao dịch từ Master sang Slave thông qua relay server.

## ✨ Tính Năng Chính

- **Copy lệnh realtime** từ Master sang Slave
- **Reverse Trading**: Master BUY → Slave SELL
- **Volume Control**: Điều chỉnh % volume (50%, 100%, 200%)
- **SL/TP Sync**: Đồng bộ Stop Loss và Take Profit
- **Symbol Mapping**: Map symbol khác nhau giữa Master và Slave
- **Đồng bộ 2 chiều**: Slave đóng lệnh → Master tự động đóng theo

## 💻 Yêu Cầu

- MetaTrader 5
- Automated Trading được bật
- Internet ổn định
- **Key** từ admin

## 📦 Cài Đặt

### Bước 1: Cấu Hình MT5
1. Tools → Options → Expert Advisors
2. Bật "Allow Automated Trading"
3. Bật "Allow WebRequest for listed URLs"
4. Thêm: `http://1.1.1.1:9090`

<!-- [HÌNH: Cấu hình MT5 Expert Advisors] -->

### Bước 2: Copy Files
Copy 2 file vào thư mục MT5:
```
C:\Users\[Username]\AppData\Roaming\MetaQuotes\Terminal\[TerminalID]\MQL5\Experts\
```
- `MasterSocketServer.ex5` - Cho tài khoản Master
- `SlaveSocketClient.ex5` - Cho tài khoản Slave

<!-- [HÌNH: Thư mục Experts với 2 file EA] -->

## ⚙️ Cấu Hình

### Master
```mql5
input string Key = "YOUR_KEY";  // Key từ admin
```

<!-- [HÌNH: Cấu hình Master EA] -->

### Slave
```mql5
input string Key = "YOUR_KEY";  // Phải giống Master
input bool ReverseTrading = true;          // Đánh ngược lệnh
input bool SyncSLTP = true;                 // Đồng bộ SL/TP
input double VolumePercent = 100.0;         // % Volume
input bool EnableBidirectionalSync = true;  // Đồng bộ 2 chiều

// Symbol mapping (Master|Slave)
input string SymbolMap1 = "GOLD|XAUUSD";   // Master GOLD → Slave XAUUSD
```

<!-- [HÌNH: Cấu hình Slave EA] -->

## 🚀 Sử Dụng

### Khởi Động
1. **Master**: Kéo `MasterSocketServer.ex5` vào chart → Nhập Key → OK
2. **Slave**: Kéo `SlaveSocketClient.ex5` vào chart → Nhập cùng Key → OK

<!-- [HÌNH: Kéo EA vào chart] -->

### Giao Dịch
- **Master**: Đặt lệnh bình thường
- **Slave**: Lệnh tự động được copy
- **Đóng lệnh**: Đồng bộ đóng lệnh

<!-- [HÌNH: Demo giao dịch Master-Slave] -->

## 🔧 Lỗi Thường Gặp

| Lỗi | Giải Pháp |
|-----|-----------|
| "AUTOMATED TRADING BỊ TẮT" | Bấm F7 hoặc Tools → Options → Allow Automated Trading |
| "Không thể kết nối" | Thêm `http://1.1.1.1:9090` vào WebRequest |
| "Key đã có Master khác" | Liên hệ admin để reset hoặc mua Key mới |
| "Key không tồn tại" | Kiểm tra Key hoặc liên hệ admin |
| "HWID MISMATCH" | Bot đã dùng trên máy khác, liên hệ admin reset |

<!-- [HÌNH: Các lỗi thường gặp và cách khắc phục] -->

## 📞 Hỗ Trợ

- **Mua Key**: [@phongdev88](https://t.me/phongdev88)
- **Reset Key**: Liên hệ admin
- **Hỗ trợ kỹ thuật**: 24/7

<!-- [HÌNH: Liên hệ hỗ trợ] -->