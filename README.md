# BT01 - Quản lý người dùng giới hạn và Truyền tải dữ liệu qua SFTP trên Windows

## Tạo user và file log

```bash
sudo adduser sftp-user
sudo mkdir -p /var/log/app-backup
sudo bash -c 'echo "Backup status: SUCCESS at 2026-10-08 10:15:00" > /var/log/app-backup/backup-check.log'
sudo chown -R root:sftp-user /var/log/app-backup
sudo chmod 750 /var/log/app-backup
sudo chmod 640 /var/log/app-backup/backup-check.log
```

## Kiểm tra trên VPS

```bash
$ id sftp-user
uid=1002(sftp-user) gid=1002(sftp-user) groups=1002(sftp-user)

$ ls -l /var/log/app-backup/backup-check.log
-rw-r----- 1 root sftp-user 47 Oct  8 10:15 /var/log/app-backup/backup-check.log
```

## Tải file bằng WinSCP

Kết nối WinSCP với tài khoản `sftp-user`, mở thư mục `/var/log/app-backup/` và tải `backup-check.log` về máy Windows.

```text
Local:  C:\Users\lephu\Downloads\backup-check.log
Remote: /var/log/app-backup/backup-check.log
Transfer completed successfully.

Backup status: SUCCESS at 2026-10-08 10:15:00
```