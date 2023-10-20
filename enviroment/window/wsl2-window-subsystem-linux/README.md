# wsl2 - window subsystem linux

## Install wsl2

1. Mở CMD/PowerShell với quyền Admin

```bash
wsl --install
```

2. Kiểm tra phiên bản wsl

```bash
wsl -l -v
```

3. Cài đặt version wsl2

```bash
wsl --set-version <distr name> 2
```

## Cài đặt os in wsl2

### Note: Ở đây mình chọn ubuntu 20.04

1. Xem list các os hiện có

```bash
wsl --list --online
```

![](https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/original/3X/f/a/fa1fb3ef9c37ea3aaa8f2721593722dd286b62e4.png)

2. Cài đặt ubuntu 20.04

```bash
wsl --install -d Ubuntu-20.04
```

3. Kiểm tra

```bash
wsl -l -v
```
