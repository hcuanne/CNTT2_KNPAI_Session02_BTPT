
# 1. Bối cảnh
So sánh 2 cách viết Prompt để trích xuất dữ liệu khách hàng bằng CREATE, Few-shot và JSON/Table.

# 2. Yêu cầu đầu ra
- Đề xuất 2 Prompt mẫu.
- Lập bảng so sánh Trade-off.
- Chọn phương án tối ưu và chạy thử.

# 3. Bài làm

## Bước 1: Đề xuất 2 Prompt

**Giải pháp 1 – Đơn giản:**

> Trích xuất tên, tuổi, email từ dữ liệu: Nguyễn Văn An, 20 tuổi, an@gmail.com. Xuất bảng Markdown.

**Giải pháp 2 – Chi tiết:**

> Role: Chuyên viên xử lý dữ liệu.
>
> Task: Trích xuất tên, tuổi, email.
>
> Action: Đọc, kiểm tra và xuất JSON.
>
> Constraints: Không tự bịa, thiếu dữ liệu ghi null.
>
> Few-shot:
>
> Input: Lê Bình, 22 tuổi, binh@gmail.com
>
> Output: {"name":"Lê Bình","age":22,"email":"binh@gmail.com"}
>
> Input: Nguyễn Văn An, 20 tuổi, an@gmail.com
>
> Chỉ trả về JSON hợp lệ.

## Bước 2: So sánh Trade-off

| Tiêu chí | Giải pháp 1 | Giải pháp 2 |
|---|---|---|
| Dễ hiểu | Cao | Trung bình |
| Token | Ít | Nhiều |
| Độ chính xác | Khá | Cao |
| Xử lý lỗi biên | Trung bình | Tốt |
| Định dạng | Markdown | JSON |
| Tái sử dụng | Trung bình | Tốt |

## Bước 3: Lựa chọn và chạy thử

**Chọn giải pháp 2** vì có cấu trúc rõ ràng, hạn chế lỗi và đảm bảo định dạng JSON.

**Kết quả chạy thử:**

    {
      "name": "Nguyễn Văn An",
      "age": 20,
      "email": "an@gmail.com"
    }

**Kết luận:** Giải pháp 2 tối ưu hơn về độ chính xác và tính nhất quán, dù tốn nhiều token hơn.
