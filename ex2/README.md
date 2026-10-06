# Bài 2: Cấu hình phân quyền Nhóm và sudoers bằng visudo

## 1. Tạo Group và User

Tạo group `devops-admin`:

```bash
sudo groupadd devops-admin
```

Tạo user `deployer`:

```bash
sudo adduser deployer
```

Thêm user `deployer` vào group:

```bash
sudo usermod -aG devops-admin deployer
```

Kiểm tra:

```bash
groups deployer
```

Kết quả cho thấy `deployer` thuộc group `devops-admin`.

## 2. Cấu hình sudoers

Mở file sudoers bằng:

```bash
sudo visudo
```

Thêm dòng:

```text
%devops-admin ALL=(ALL) NOPASSWD: /usr/bin/systemctl start *, /usr/bin/systemctl stop *, /usr/bin/systemctl restart *, /usr/bin/systemctl status *
```

Cấu hình trên cho phép các user thuộc group `devops-admin` thực hiện các lệnh `systemctl start`, `stop`, `restart`, `status` mà không cần nhập mật khẩu.

## 3. Kiểm tra

Chuyển sang user `deployer`:

```bash
su - deployer
```

Kiểm tra quyền:

```bash
sudo -l
```

Kết quả hiển thị quyền `systemctl` với `NOPASSWD`.

Kiểm tra restart service:

```bash
sudo systemctl restart cron
```

Lệnh thực hiện thành công mà không yêu cầu nhập mật khẩu.

## 4. Kết luận

Đã hoàn thành cấu hình phân quyền cho group `devops-admin`. User `deployer` chỉ được phép quản lý các service bằng các thao tác `start`, `stop`, `restart`, `status` và không được cấp toàn quyền sudo/root.
