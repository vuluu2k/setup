# Editor linux

Để đặt trình soạn thảo mặc định thành vim thay vì nano trong Ubuntu, bạn có thể làm theo các bước sau:

1. Mở terminal và chạy lệnh:

```bash
sudo update-alternatives --config editor
```

2. Trong danh sách các lựa chọn, chọn số thứ tự tương ứng với vim.
3. Lưu lại thay đổi bằng cách nhấn phím Enter.
4. Kiểm tra lại xem vim đã được đặt làm trình soạn thảo mặc định bằng cách chạy:

```bash
select-editor
```

Nó sẽ hiển thị vim là trình soạn thảo mặc định.

Từ giờ trở đi, mỗi khi bạn chạy các lệnh cần mở trình soạn thảo như sudo nano, nano, vi, vim, nó sẽ tự động mở vim thay vì nano.
