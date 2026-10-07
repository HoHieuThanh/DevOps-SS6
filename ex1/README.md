# Bài 1: Khảo sát FHS và Phân quyền File/Folder nâng cao

## 1. Tạo cấu trúc thư mục

Tạo thư mục `public` và `logs`:

```bash
sudo mkdir -p /var/www/my-app/public
sudo mkdir -p /var/www/my-app/logs
```

## 2. Phân quyền thư mục

Cấp quyền `750` cho thư mục `public`:

```bash
sudo chmod 750 /var/www/my-app/public
```

Cấp quyền `770` cho thư mục `logs`:

```bash
sudo chmod 770 /var/www/my-app/logs
```

## 3. Thiết lập Owner và Group

Gán tài khoản hiện tại làm chủ sở hữu và nhóm `www-data`:

```bash
sudo chown -R $USER:www-data /var/www/my-app
```

## 4. Kiểm tra

Kiểm tra cấu trúc và quyền:

```bash
ls -la /var/www/my-app
```

Kết quả mong đợi:

```text
drwxr-x---  ...  acer  www-data  public
drwxrwx---  ...  acer  www-data  logs
```

Trong đó:

* `public`: quyền `750` — Owner đọc/ghi/truy cập, Group đọc/truy cập, Others không có quyền.
* `logs`: quyền `770` — Owner và Group có toàn quyền, Others không có quyền.
* Owner là tài khoản non-root `acer`.
* Group là `www-data`.

## 5. Kết luận

Đã hoàn thành việc tạo cấu trúc thư mục `/var/www/my-app`, thiết lập quyền truy cập bằng octal và cấu hình Owner/Group phù hợp cho thư mục `public` và `logs`.
