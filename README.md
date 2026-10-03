## Mục tiêu

Loại bỏ `credentials.txt` khỏi phạm vi theo dõi của Git nhưng vẫn giữ tệp ở thư mục làm việc cục bộ, đồng thời cấu hình Git bỏ qua tệp này trong các lần commit sau.

## Các lệnh đã thực hiện

Sau khi `credentials.txt` bị commit nhầm, tệp được gỡ khỏi Git index bằng lệnh:

```bash
git rm --cached Ex4/credentials.txt
```

Tùy chọn `--cached` chỉ xóa tệp khỏi index của Git, không xóa tệp vật lý trên ổ đĩa. Sau đó, quy tắc sau được thêm vào `Ex4/.gitignore`:

```gitignore
credentials.txt
```

Các thay đổi được thêm vào staging area và commit gần nhất được sửa bằng:

```bash
git add Ex4/.gitignore Ex4/README.md
git commit --amend -m "chore: ignore credentials and document cleanup"
```

## Kết quả kiểm tra

Kiểm tra trạng thái repository:

```bash
git status
```

`credentials.txt` không xuất hiện trong danh sách staged hoặc modified. Có thể xác nhận tệp vẫn tồn tại cục bộ và đang bị bỏ qua bằng:

```bash
test -f Ex4/credentials.txt
git check-ignore -v Ex4/credentials.txt
```

Kiểm tra thông điệp commit gần nhất:

```bash
git log -n 1 --pretty=format:"%s"
```

Kết quả:

```text
chore: ignore credentials and document cleanup
```