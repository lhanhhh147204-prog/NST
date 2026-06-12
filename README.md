# Dự Án Phân Tích Hình Thái Nhiễm Sắc Thể (NST)

Dự án sử dụng kiến trúc mạng **Hybrid Attention U-Net** kết hợp với **Knowledge Distillation** để nhận diện và tách các Nhiễm Sắc Thể (NST) bị chồng chéo.

Dự án này sử dụng công cụ [uv](https://github.com/astral-sh/uv) để quản lý dependencies và môi trường ảo, giúp việc cài đặt siêu nhanh và đảm bảo tính nhất quán trên mọi máy.

## 🛠️ Hướng dẫn cài đặt cho người mới tải code về

### 1. Cài đặt `uv`
Nếu máy bạn chưa có `uv`, bạn có thể cài đặt cực nhanh bằng một trong các cách sau:

- **Windows (PowerShell):**
  ```powershell
  irm https://astral.sh/uv/install.ps1 | iex
  ```
- **macOS / Linux:**
  ```bash
  curl -LsSf https://astral.sh/uv/install.sh | sh
  ```
- Hoặc dùng **pip** (nếu đã có Python):
  ```bash
  pip install uv
  ```

### 2. Cài đặt môi trường và các gói thư viện
Mở Terminal tại thư mục của dự án và chạy:

```bash
uv sync
```

**Lệnh này sẽ làm gì?**
- Tự động đọc file `pyproject.toml` và `uv.lock` (nếu có).
- Tự động tạo một môi trường ảo (virtual environment) biệt lập trong thư mục `.venv`.
- Cài đặt chính xác các phiên bản thư viện cần thiết, giúp tránh tuyệt đối hiện tượng xung đột môi trường hay "máy tôi chạy được nhưng máy bạn thì không".

### 3. Chạy chương trình

Bạn có thể sử dụng `uv run` để chạy trực tiếp script mà không cần thủ công kích hoạt (activate) môi trường ảo:

```bash
# Xem hướng dẫn các tham số
uv run main.py --help

# Chạy toàn bộ pipeline từ chuẩn bị dữ liệu đến khi đánh giá
uv run main.py --step all

# Chạy từng bước cụ thể (ví dụ: huấn luyện Teacher model)
uv run main.py --step train_teacher
```

---

## 👨‍💻 Dành cho người phát triển (Thêm thư viện mới)

Nếu bạn code thêm tính năng và cần thêm thư viện mới (ví dụ `matplotlib`), chỉ cần chạy:
```bash
uv add matplotlib
```
Lệnh này sẽ tự động tải thư viện, cập nhật `pyproject.toml` và ghi đè file `uv.lock`. Hãy nhớ **commit cả file `pyproject.toml` và `uv.lock`** lên git nhé!
