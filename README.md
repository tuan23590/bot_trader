# 🤖 Bot Copy Trade MT5 - Hướng Dẫn Sử Dụng

## 📋 Bot làm gì?

Bot tự động **SAO CHÉP** lệnh giao dịch từ tài khoản **MASTER** sang tài khoản **SLAVE**.

- 💻 **MASTER**: Tài khoản giao dịch chính (tự động ghi dữ liệu)
- 📱 **SLAVE**: Tài khoản sao chép (tự động copy lệnh từ MASTER)

---

## 🚀 Cài Đặt Nhanh

### ⚡ Bước 1: Cài trên MASTER
1. Mở MT5 tài khoản **MASTER**
2. Kéo thả file `bot.ex5` vào chart
3. Chọn: **Mode = MODE_MASTER**
4. Nhấn **OK**

### ⚡ Bước 2: Cài trên SLAVE  
1. Mở MT5 tài khoản **SLAVE**
2. Kéo thả file `bot.ex5` vào chart
3. Chọn: **Mode = MODE_SLAVE**
4. Cấu hình tham số (xem bên dưới)
5. Nhấn **OK**

---

## ⚙️ Cấu Hình SLAVE

### 🎯 Cài Đặt Cơ Bản

| Tham Số | Giá Trị | Ý Nghĩa |
|----------|---------|---------|
| **Mode** | `MODE_SLAVE` | Chế độ sao chép |
| **ReverseOrders** | `true` hoặc `false` | `true` = Đảo ngược (BUY↔SELL)<br>`false` = Copy y hệt |
| **VolumeAdder** | Số thập phân | `0.2` = Thêm 0.2 lots<br>`-0.1` = Giảm 0.1 lots |

### 🔗 Cấu Hình Symbols

**⚠️ QUAN TRỌNG**: Bot chỉ copy những symbols bạn cấu hình. Không cấu hình = không copy!

```
Symbol_Bind_1 = "EURUSD|EURUSD"     ← Copy EURUSD
Symbol_Bind_2 = "XAUUSD|GOLD"       ← MASTER: XAUUSD → SLAVE: GOLD  
Symbol_Bind_3 = "GBPUSD|GBPUSD"     ← Copy GBPUSD
...
```

**Cú pháp**: `"SymbolMaster|SymbolSlave"`

---

## 📖 Ví Dụ Cấu Hình

### 🔄 Copy Thường (Follow)
```
Mode = MODE_SLAVE
ReverseOrders = false
VolumeAdder = 0.0
Symbol_Bind_1 = "EURUSD|EURUSD"
Symbol_Bind_2 = "GBPUSD|GBPUSD"
```
**Kết quả**: MASTER BUY 1.0 lot → SLAVE BUY 1.0 lot

### 🔀 Copy Đảo Ngược (Hedge)
```
Mode = MODE_SLAVE
ReverseOrders = true
VolumeAdder = 0.0
Symbol_Bind_1 = "EURUSD|EURUSD"
```
**Kết quả**: MASTER BUY 1.0 lot → SLAVE SELL 1.0 lot

### 📈 Copy Với Volume Lớn Hơn
```
Mode = MODE_SLAVE
ReverseOrders = false
VolumeAdder = 0.5
Symbol_Bind_1 = "EURUSD|EURUSD"
```
**Kết quả**: MASTER BUY 1.0 lot → SLAVE BUY 1.5 lot

---

## ✅ Checklist Trước Khi Chạy

### Trên Cả 2 Tài Khoản:
- [ ] Nhấn nút **"AutoTrading"** trên thanh công cụ MT5 (phải màu xanh)
- [ ] Chuột phải bot → **Properties** → **Common** → Check **"Allow Algo Trading"**

---

## 🔍 Khắc Phục Lỗi

### ❌ "Bot không khởi động"
**Lỗi**: `🛑 BOT KHÔNG THỂ KHỞI ĐỘNG - AutoTrading BỊ TẮT`  
**Sửa**: Nhấn nút **"AutoTrading"** trên thanh công cụ MT5

### ❌ "Bot không copy lệnh"
**Lỗi**: `🚫 CHẶN Symbol không được cấu hình: EURUSD`  
**Sửa**: Thêm `Symbol_Bind_1 = "EURUSD|EURUSD"`

### ❌ "SLAVE không kết nối MASTER"
**Lỗi**: `⚠️ SLAVE: Không kết nối MASTER`  
**Sửa**: 
- Kiểm tra MASTER đã chạy chưa?
- Khởi động lại cả 2 bot

### ❌ "Lỗi mở lệnh"
**Lỗi**: `❌ SLAVE: LỖI MỞ LỆNH - Mã lỗi: 134`  
**Sửa**:
- Symbol có trong Market Watch không?
- Tài khoản đủ tiền không?
- AutoTrading đã bật chưa?

---

## 📊 Theo Dõi Hoạt Động

### 📈 Trên Chart SLAVE
Bot hiển thị thống kê real-time:
```
MODE: SLAVE (REVERSE)

📊 TỔNG VOLUME: 25.50 lots
📈 TỔNG LỆNH: 48 lệnh  
🔄 ĐANG MỞ: 3 lệnh

• EURUSD: 15 lệnh (8.30)
• GBPUSD: 12 lệnh (5.20)
• XAUUSD: 8 lệnh (12.00)
```

### 📝 Trong Tab Experts
Xem log chi tiết để theo dõi hoạt động và lỗi

---

## 🛡️ Lưu Ý An Toàn

- ⚠️ **Test trước** trên tài khoản demo
- ⚠️ **Đặt volume hợp lý** (không quá lớn)
- ⚠️ **Theo dõi thường xuyên** khi chạy
- ⚠️ **Cấu hình symbols cẩn thận** (chỉ copy symbols mong muốn)

---

## 🆘 Cần Hỗ Trợ?

Khi gặp lỗi, cung cấp thông tin:
- Cấu hình bot (Mode, ReverseOrders, VolumeAdder, Symbol_Bind_X)
- Log lỗi từ tab **Experts**
- Broker và phiên bản MT5

---

**🎯 Mục tiêu**: Bot chạy im lặng, copy lệnh tự động, báo lỗi khi cần thiết!** 