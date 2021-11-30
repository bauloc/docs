# THỦ THUẬT LẬP TRÌNH FLUTTER
# Cập nhật ngày 26/11/2021

## CÀI ĐẶT
1. Tải bộ cài đặt ở link này:
```
https://docs.flutter.dev/get-started/install/macos
```
2. Giải nén và copy folder flutter bỏ vào thư mục
```
/Users/bauloc/Development/flutter
```
3. Add PATH
```
sudo nano /etc/paths
/Users/bauloc/Development/flutter/bin
```
Nếu chưa đc thì đọc tài liệu: https://stackoverflow.com/questions/50652071/flutter-command-not-found

4. Kiểm tra OK chưa
```
flutter doctor
```

## TẠO PROJECT
Tạo 1 project
```
flutter create my_project_name
```

Ví dụ cần tạo project với bundle id **bauloc.app.test1**
```
flutter create --org bauloc.app test1
```

## SỬA LỖI KHI CLONE PROJECT TỪ GIT VỀ RUN KHÔNG ĐƯỢC