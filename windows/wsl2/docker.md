# Để cài docker chạy trên nền wsl2 thì bạn cần cài đặt wsl 2 trước nhé
# Tải docker desktop về trước

<a href="https://www.docker.com/products/docker-desktop/"><h1>Download docker desktop</h1></a>

## 1. Bắt đầu cài đặt cấu hình phù hợp để chạy docker trên wsl2

<b>Trong verison hệ điểu hành ảo mà bạn chọn ơ đây mình chọn ubuntu 20.04 mở terminal của nó lên</b>

```shell
sudo vim /etc/wsl.conf
```
<br>
<strong>Thêm đoạn code sau vào dưới cuối để limit memory và cho phép localhost trên máy windows và wsl2 thông nhau</strong>
<br>

```console
[wsl2]
memory=6GB
swap=0
localhostForwarding=true
```

## 2. Trong Docker desktop 

<ul>
  <li>
    Tích chọn <strong>Enable the experimental WSL2 based engine</strong> 
  </li>
  <li>
    Bỏ tích <strong>Expose tcp://localhost:2375</strong> 
    <img src="https://images.viblo.asia/dc34682d-7c96-4586-8a70-28befdca80c4.png"/>
  </li>
  <li>
    Bật WSL2 integration với Distro dùng WSL2
    <img src="https://images.viblo.asia/dc34682d-7c96-4586-8a70-28befdca80c4.png"/>
  </li>
  <li>Apply & Restart rồi mọi thứ sẽ chạy như bình thường.</li>
</ul>