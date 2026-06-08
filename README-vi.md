<div align="center">
<h1 align="center">MoneyPrinterTurbo 💸</h1>

<p align="center">
  <a href="https://github.com/harry0703/MoneyPrinterTurbo/stargazers"><img src="https://img.shields.io/github/stars/harry0703/MoneyPrinterTurbo.svg?style=for-the-badge" alt="Stargazers"></a>
  <a href="https://github.com/harry0703/MoneyPrinterTurbo/issues"><img src="https://img.shields.io/github/issues/harry0703/MoneyPrinterTurbo.svg?style=for-the-badge" alt="Issues"></a>
  <a href="https://github.com/harry0703/MoneyPrinterTurbo/network/members"><img src="https://img.shields.io/github/forks/harry0703/MoneyPrinterTurbo.svg?style=for-the-badge" alt="Forks"></a>
  <a href="https://github.com/harry0703/MoneyPrinterTurbo/blob/main/LICENSE"><img src="https://img.shields.io/github/license/harry0703/MoneyPrinterTurbo.svg?style=for-the-badge" alt="License"></a>
</p>

<h3><a href="README.md">简体中文</a> | <a href="README-en.md">English</a> | Tiếng Việt</h3>

</div>

Chỉ cần cung cấp **chủ đề** hoặc **từ khóa** cho video, công cụ sẽ tự động tạo kịch bản, tìm tư liệu video, tạo phụ đề, chèn nhạc nền và xuất ra video ngắn độ phân giải cao — hoàn toàn tự động.

## Tính năng nổi bật

- Kiến trúc MVC rõ ràng, hỗ trợ cả **API** và **giao diện Web**
- Tạo kịch bản video bằng AI hoặc nhập kịch bản tùy chỉnh
- Hỗ trợ video dọc **9:16** (TikTok/Reels) và ngang **16:9** (YouTube)
- Tạo nhiều video cùng lúc, chọn video ưng ý nhất
- Tổng hợp giọng đọc **tiếng Việt** tự nhiên (Azure Edge TTS miễn phí)
- Tạo phụ đề tự động, tuỳ chỉnh font, vị trí, màu sắc, cỡ chữ
- Nhạc nền ngẫu nhiên hoặc tùy chọn, điều chỉnh âm lượng
- Hỗ trợ nhiều nhà cung cấp LLM: **Groq** (miễn phí), OpenAI, Gemini, DeepSeek, Ollama,...
- Tư liệu video từ Pexels, Pixabay (miễn phí) hoặc file cục bộ

---

## Yêu cầu hệ thống

- **Windows 10/11** (64-bit) — khuyến nghị
- RAM tối thiểu **4 GB**, khuyến nghị **8 GB** trở lên
- Không bắt buộc có GPU

| Thành phần | Tối thiểu | Khuyến nghị |
|---|---|---|
| CPU | 4 nhân | 6–8 nhân |
| RAM | 4 GB | 8 GB trở lên |
| GPU | Không cần | VRAM 4 GB+ |

---

## Cài đặt trên Windows

Có 3 cách để chạy MoneyPrinterTurbo trên Windows:

| Cách | Độ khó | Phù hợp |
|---|---|---|
| [Docker Desktop](#cách-1-docker-desktop-khuyến-nghị) | Dễ | Người dùng phổ thông |
| [Gói cài sẵn (.zip)](#cách-2-gói-cài-sẵn-zip) | Rất dễ | Thử nhanh không cần cài đặt |
| [Python thủ công](#cách-3-python-thủ-công) | Trung bình | Developer |

---

## Cách 1: Docker Desktop (Khuyến nghị)

Docker tạo môi trường cô lập, không ảnh hưởng đến hệ thống, dễ cập nhật.

### Bước 1 — Cài Docker Desktop

1. Tải tại [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/)
2. Cài đặt → khởi động lại máy nếu được yêu cầu
3. Mở Docker Desktop, chờ icon ở taskbar chuyển sang trạng thái **Running** (màu xanh)

> **Lưu ý WSL2:** Nếu Windows yêu cầu bật WSL2, làm theo hướng dẫn tại:
> - [Cài đặt WSL2](https://learn.microsoft.com/vi-vn/windows/wsl/install)
> - [Docker + WSL2](https://learn.microsoft.com/vi-vn/windows/wsl/tutorials/wsl-containers)

### Bước 2 — Tải mã nguồn

Mở **Command Prompt** hoặc **PowerShell** và chạy:

```powershell
git clone https://github.com/ThuanVD/MoneyPrinterTurbo.git
cd MoneyPrinterTurbo
```

> Nếu chưa có Git, tải tại [git-scm.com](https://git-scm.com/download/win). Hoặc tải thẳng file ZIP từ GitHub rồi giải nén.

### Bước 3 — Cấu hình (tùy chọn)

Nếu muốn tùy chỉnh trước khi chạy, sao chép file cấu hình mẫu:

```powershell
copy config.example.toml config.toml
```

Mở `config.toml` bằng Notepad và điền API key (xem [Cấu hình API Key](#cấu-hình-api-key) bên dưới).

> Nếu bỏ qua bước này, ứng dụng vẫn chạy và bạn có thể cấu hình trực tiếp qua giao diện web.

### Bước 4 — Khởi động

```powershell
docker compose up -d
```

Lần đầu chạy sẽ tải image (~vài phút tùy tốc độ mạng). Từ lần sau khởi động rất nhanh.

### Bước 5 — Mở giao diện

Mở trình duyệt (Chrome hoặc Edge) và truy cập:

- **Giao diện Web:** [http://127.0.0.1:8501](http://127.0.0.1:8501)
- **API Docs:** [http://127.0.0.1:8080/docs](http://127.0.0.1:8080/docs)

### Dừng / Khởi động lại

```powershell
# Dừng
docker compose down

# Khởi động lại
docker compose up -d

# Xem log nếu có lỗi
docker compose logs webui
```

---

## Cách 2: Gói cài sẵn (.zip)

Dành cho người muốn thử nhanh, không cần cài Docker hay Python.

1. Tải gói từ Google Drive: [MoneyPrinterTurbo v1.2.6](https://drive.google.com/file/d/1HsbzfT7XunkrCrHw5ncUjFX8XX4zAuUh/view?usp=sharing)
2. Giải nén ra bất kỳ thư mục nào (ví dụ `D:\MoneyPrinterTurbo`)
3. **Bắt buộc:** Double-click `update.bat` để cập nhật lên phiên bản mới nhất
4. Double-click `start.bat` để khởi động

> Trình duyệt sẽ tự mở. Nếu trang trắng, dùng **Chrome** hoặc **Edge**.

---

## Cách 3: Python thủ công

### Bước 1 — Cài đặt các công cụ cần thiết

**Python 3.11:**
Tải tại [python.org/downloads](https://www.python.org/downloads/) — trong quá trình cài nhớ tick chọn **"Add Python to PATH"**

**FFmpeg:**
1. Tải tại [ffmpeg.org/download.html](https://ffmpeg.org/download.html) → chọn **Windows builds**
2. Giải nén vào `C:\ffmpeg`
3. Thêm `C:\ffmpeg\bin` vào biến môi trường PATH:
   - Tìm kiếm "Environment Variables" trong Start Menu
   - Chọn **"Edit the system environment variables"**
   - Click **"Environment Variables"** → chọn `Path` → **Edit** → **New** → nhập `C:\ffmpeg\bin`

**Git:** Tải tại [git-scm.com](https://git-scm.com/download/win) (nếu chưa có)

### Bước 2 — Tải mã nguồn

```powershell
git clone https://github.com/ThuanVD/MoneyPrinterTurbo.git
cd MoneyPrinterTurbo
```

### Bước 3 — Cài dependencies (cách nhanh với uv)

```powershell
pip install uv
uv python install 3.11
uv sync --frozen
```

Hoặc dùng pip thông thường:

```powershell
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

### Bước 4 — Cấu hình

```powershell
copy config.example.toml config.toml
```

Mở `config.toml` và cấu hình theo hướng dẫn bên dưới.

### Bước 5 — Khởi động giao diện Web

```powershell
webui.bat
```

---

## Cấu hình API Key

Mở file `config.toml` (hoặc cấu hình trực tiếp trên giao diện web sau khi khởi động).

### LLM (AI tạo kịch bản)

Cần ít nhất một nhà cung cấp LLM để AI tạo nội dung kịch bản.

**Groq — Miễn phí, nhanh, khuyến nghị cho người mới:**
1. Đăng ký tại [console.groq.com](https://console.groq.com)
2. Vào **API Keys** → **Create API Key**
3. Điền vào `config.toml`:

```toml
llm_provider = "groq"
groq_api_key = "gsk_xxxxxxxxxxxxxxxxxxxx"
groq_model_name = "llama-3.3-70b-versatile"
```

**DeepSeek — Giá rẻ, chất lượng cao:**
1. Đăng ký tại [platform.deepseek.com](https://platform.deepseek.com)
2. Điền vào `config.toml`:

```toml
llm_provider = "deepseek"
deepseek_api_key = "sk-xxxxxxxxxxxxxxxxxxxx"
deepseek_model_name = "deepseek-chat"
```

**Gemini — Miễn phí với Google account:**
1. Lấy key tại [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
2. Điền vào `config.toml`:

```toml
llm_provider = "gemini"
gemini_api_key = "AIza_xxxxxxxxxxxxxxxxxxxx"
gemini_model_name = "gemini-2.5-flash"
```

### Nguồn video

Cần ít nhất một trong hai (hoặc dùng file cục bộ, không cần key):

**Pixabay — Miễn phí:**
1. Đăng ký tại [pixabay.com](https://pixabay.com) → vào [pixabay.com/api/docs](https://pixabay.com/api/docs/)
2. API Key hiển thị ngay trên trang sau khi đăng nhập

**Pexels — Miễn phí:**
1. Đăng ký tại [pexels.com/api](https://www.pexels.com/api/)
2. API Key gửi qua email

```toml
pexels_api_keys = ["your_pexels_key"]
pixabay_api_keys = ["your_pixabay_key"]
```

> Nếu chưa có key, chọn **"Tệp cục bộ"** trong phần Nguồn Video và upload video/ảnh từ máy.

---

## Cài đặt mặc định tiếng Việt

Dự án này đã được cấu hình sẵn cho tiếng Việt:

| Cài đặt | Giá trị mặc định |
|---|---|
| Ngôn ngữ giao diện | Tiếng Việt |
| Ngôn ngữ kịch bản | vi-VN |
| Giọng đọc TTS | vi-VN-HoaiMyNeural (miễn phí) |
| Font phụ đề | UTM Kabel KT (hỗ trợ đầy đủ tiếng Việt có dấu) |

Để thay đổi, chỉnh trực tiếp trong `config.toml` hoặc qua giao diện web.

---

## Xử lý lỗi thường gặp trên Windows

### Phụ đề hiển thị ô vuông thay vì chữ có dấu

Font mặc định không hỗ trợ tiếng Việt. Trong giao diện web, phần **Cài Đặt Phụ Đề**, đổi **Phông Chữ Phụ Đề** sang `UTM Kabel KT.ttf`.

### Docker không khởi động được

- Đảm bảo **Docker Desktop** đang chạy (icon ở taskbar)
- Nếu lỗi WSL2: chạy PowerShell với quyền Admin và nhập `wsl --update`
- Thử khởi động lại Docker Desktop

### Lỗi `docker: command not found` trong PowerShell

Docker Desktop chưa được thêm vào PATH. Thử khởi động lại máy tính sau khi cài Docker Desktop.

### Trang web mở ra nhưng trắng hoặc lỗi

- Chờ thêm 10–20 giây (lần đầu khởi động chậm hơn)
- Dùng **Chrome** hoặc **Edge** thay vì Firefox
- Kiểm tra log: `docker compose logs webui`

### Không tạo được video — lỗi LLM API

Kiểm tra API key đã điền đúng chưa. Groq có thể giới hạn request theo ngày ở tài khoản free — thử đổi sang Gemini hoặc DeepSeek.

---

## Cập nhật phiên bản mới

### Docker

```powershell
git pull
docker compose down
docker compose build
docker compose up -d
```

### Gói cài sẵn

Double-click `update.bat`

### Python thủ công

```powershell
git pull
uv sync --frozen
```

---

## Giọng đọc tiếng Việt

Danh sách đầy đủ các giọng: [docs/voice-list.txt](./docs/voice-list.txt)

Một số giọng tiếng Việt miễn phí (Azure Edge TTS):

| Giọng | Giới tính | Phong cách |
|---|---|---|
| vi-VN-HoaiMyNeural | Nữ | Tự nhiên, trung tính |
| vi-VN-NamMinhNeural | Nam | Tự nhiên, trung tính |

Chọn giọng trong giao diện web hoặc thêm vào `config.toml`:

```toml
[ui]
tts_server = "azure-tts-v1"
voice_name = "vi-VN-HoaiMyNeural-Female"
```

---

## Tạo phụ đề

Có 2 chế độ tạo phụ đề:

- **edge** (mặc định): Dùng timestamp của Edge TTS — nhanh, không cần GPU
- **whisper**: Dùng AI nhận dạng giọng nói cục bộ — chính xác hơn, cần tải model ~3GB

Cấu hình trong `config.toml`:

```toml
subtitle_provider = "edge"   # hoặc "whisper"
```

---

## Liên kết hữu ích

- GitHub gốc: [github.com/harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo)
- Thử online không cần cài đặt: [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/harry0703/MoneyPrinterTurbo/blob/main/docs/MoneyPrinterTurbo.ipynb)
- Tài liệu API: [http://127.0.0.1:8080/docs](http://127.0.0.1:8080/docs) (sau khi khởi động)
