# Bài 3: Cấu hình tường lửa UFW và chẩn đoán cổng mạng

## 1. Cấu hình UFW

Thiết lập chính sách mặc định:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Cho phép kết nối SSH qua port 22:

```bash
sudo ufw allow 22/tcp
```

Cho phép ứng dụng Web qua port 8080:

```bash
sudo ufw allow 8080/tcp
```

Kích hoạt tường lửa:

```bash
sudo ufw enable
```

## 2. Kiểm tra trạng thái UFW

Kiểm tra bằng:

```bash
sudo ufw status verbose
```

Kết quả:

```text
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
8080/tcp                   ALLOW IN    Anywhere
22/tcp (v6)                ALLOW IN    Anywhere (v6)
8080/tcp (v6)              ALLOW IN    Anywhere (v6)
```

## 3. Kiểm tra cổng mạng

Sử dụng lệnh:

```bash
ss -tlnp
```

Lệnh này dùng để kiểm tra các cổng TCP đang lắng nghe trên máy chủ.
