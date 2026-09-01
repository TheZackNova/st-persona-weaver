# 🧙‍♂️ Persona Weaver (Trình tạo nhân vật User)

[Tiếng Việt] | [中文](#chinese) | [English](#english)

Tiện ích mở rộng gốc cho SillyTavern. Dùng AI để tạo, trau chuốt và quản lý User Persona của bạn, kèm chế độ so sánh thông minh và đồng bộ World Info.

> **Bản Việt hoá**: toàn bộ giao diện, nút bấm, thông báo, prompt gửi cho AI và mẫu YAML đã chuyển sang tiếng Việt.

### Về khoá trong mẫu YAML

Khoá viết tự nhiên được: `Họ và tên:`, `Đặc điểm ngoại hình:`, `Hành trang & Tài sản:`, `Kỹ năng tối thượng (Ultimate Skill):` — dấu cách, gạch ngang, ngoặc, `/` và `&` đều hợp lệ. **Ký tự duy nhất bị cấm là dấu hai chấm**, vì đó là thứ ngăn cách khoá với giá trị.

AI được yêu cầu chép khoá **y nguyên từng ký tự** theo mẫu đang dùng, không dịch, không đổi thứ tự, không đổi cách viết. Nếu kết quả trả về sai kiểu khoá so với mẫu, đó là lỗi — hãy báo.

Hai mẫu mặc định kèm theo cũng viết bằng dấu cách (`Thông tin cơ bản`, `Câu chuyện nền`, `Thời trung niên (35 đến nay)`). Nếu bác đang dùng mẫu mặc định bản cũ — tiếng Trung hoặc bản Việt nối bằng gạch dưới — nó sẽ **tự chuyển** sang bản mới khi mở lại. Mẫu bác đã tự sửa thì giữ nguyên, không bị đụng tới.

## ✨ Tính năng chính

*   **Sinh nội dung bằng AI**: từ một mô tả ngắn bằng ngôn ngữ tự nhiên (hoặc mẫu YAML có sẵn), tự động tạo ra hồ sơ nhân vật có cấu trúc, chi tiết.
*   **Trau chuốt sâu & so sánh thông minh**:
    *   Chưa vừa ý? Nhập góp ý, AI sẽ viết lại.
    *   Chế độ **Diff** hiển thị trực quan phần thay đổi trước/sau, cho phép giữ lại từng đoạn hoặc sửa trực tiếp.
*   **Hộp bản nháp**: tự động hoặc thủ công lưu kết quả vào bản ghi, không mất ý tưởng, nạp lại bằng một cú nhấp.
*   **Liên kết World Info**: tự phát hiện World Info đang gắn với nhân vật, ghi thiết lập vào đó như một mục mới.
*   **Lấy nội dung từ Fandom Wiki**: dán link `*.fandom.com/wiki/...` vào ô yêu cầu, tiện ích tự nhận ra và hiện nút tải. Trang chính **và các mục con** (`/Abilities & gear`, `/Relationships`, `/Chronology`, …) được rút gọn thành văn bản thuần rồi đính kèm làm tham chiếu cho lần sinh kế tiếp.
*   **API riêng**: cấu hình một API độc lập (OpenAI, DeepSeek, …) để chạy nền, không đụng tới ngữ cảnh và cấu hình model của cuộc chat chính.
*   **Hỗ trợ điện thoại**: giao diện tối ưu cho cảm ứng, vuốt và thao tác nổi.

## 📦 Cài đặt

1.  **Khuyến nghị trước**: cài và bật [TavernHelper (JS-Slash-Runner)](https://github.com/n0vi028/JS-Slash-Runner) để thao tác World Info đầy đủ nhất (không bắt buộc).
2.  Mở trang **Extensions** của SillyTavern.
3.  Nhấn **Install Extension**.
4.  Dán địa chỉ kho: `https://github.com/sisisisilviaxie-star/st-persona-weaver`
5.  Nhấn **Save** rồi tải lại trang.

## 📖 Dùng nhanh

1.  Sau khi cài, phía trên ô nhập liệu sẽ có **biểu tượng đũa phép** (<i class="fa-solid fa-wand-magic-sparkles"></i>), nhấn để mở bảng điều khiển.
2.  **Tạo**: nhập yêu cầu ở tab Nhân vật rồi nhấn nút tạo.
3.  **Trau chuốt**: bôi đen một đoạn trong kết quả rồi nhấn nút “Sửa đoạn này”, hoặc nhập góp ý ở ô bên dưới.
4.  **Lưu**: nhấn “Lưu vào bản ghi” để cất vào bản nháp, hoặc “Ghi đè nhân vật hiện tại” để áp dụng ngay.

### Dùng Fandom Wiki làm tư liệu

1.  Dán link trang Fandom vào ô yêu cầu, ví dụ `https://genshin-impact.fandom.com/vi/wiki/Furina`. Cả dạng có mã ngôn ngữ (`/vi/wiki/`) lẫn dạng không có đều nhận.
2.  Thanh xanh hiện ra bên dưới ô nhập — nhấn **Tải nội dung Wiki**.
3.  Link trong ô yêu cầu được thay bằng nhãn gọn `[Wiki: Tên trang]`; nội dung nằm sẵn trong bộ nhớ tạm. Dòng trạng thái cho biết đã gộp mấy mục con và tên của chúng.
4.  Nhấn nút tạo. Nội dung wiki (tối đa 15.000 ký tự) được đính kèm làm khối tham chiếu.

**Mục con.** Nhiều wiki nhân vật tách tư liệu ra trang riêng — `Carrera` có thêm `Carrera/Abilities & gear`, `Carrera/Chronology`, `Carrera/Relationships`. Tiện ích tự liệt kê và tải tối đa 12 mục con trong **một** lần gọi API, đánh dấu từng phần bằng `### Tên trang`.

Hai loại mục con bị bỏ: trang ảnh (`/Gallery`, `/Image Gallery`, `/Images`, `/Thư viện`) vì hầu như chỉ có chú thích và tên tệp, và mục con đã được nhúng sẵn trong trang chính vì sẽ bị đếm hai lần. Chỉ khớp khi **cả đoạn tên** trùng — `/Gallery of Heroes` vẫn được giữ.

Nếu tổng vượt 15.000 ký tự, ngân sách được chia đều rồi rót phần thừa của mục ngắn sang mục dài — một mục con khổng lồ không thể chiếm hết chỗ của trang chính, và phần bị cắt có đánh dấu `…(đã cắt bớt)`. Lấy mục con thất bại thì trang chính vẫn dùng được bình thường.

Bộ nhớ tạm **bị xoá sau mỗi lần sinh** để không âm thầm gắn lại tư liệu cũ vào các yêu cầu sau. Cần dùng lại thì tải lại — thanh sẽ tự hiện khi nhãn/link vẫn còn trong ô yêu cầu.

Tính năng gọi thẳng MediaWiki API công khai của Fandom (`api.php?...&origin=*`) từ trình duyệt, không qua máy chủ trung gian và không gửi kèm dữ liệu nào của bác.

> **Nâng cấp từ bản tiếng Trung**: prompt mặc định cũ và mẫu YAML mặc định cũ sẽ tự chuyển sang bản tiếng Việt khi mở lại. Prompt hoặc mẫu bạn đã tự sửa được giữ nguyên — muốn dùng bản tiếng Việt thì nhấn “Khôi phục mặc định”.

---

<a name="chinese"></a>
## 中文

SillyTavern 原生扩展插件。旨在利用 AI 智能生成、深度润色和管理您的 User Persona（用户人设），支持智能对比编辑与世界书自动联动。

本仓库为越南语本地化版本：界面、提示词与 YAML 模版均已改为越南语。

*   **AI 智能生成**：根据简单的自然语言描述（或内置 YAML 模版），自动生成结构化、高质量的用户人设。
*   **深度润色 & 智能对比**：提供 Diff（差异对比）视图，直观展示修改前后的变化。
*   **草稿箱系统**：自动或手动保存生成记录到草稿箱。
*   **世界书联动**：自动检测当前绑定的世界书，将设定作为条目一键写入。
*   **独立 API 支持**：支持配置独立的 API（如 OpenAI、DeepSeek 等）进行后台生成。
*   **移动端适配**：优化的 UI 设计，支持手机端触摸滑动与悬浮操作。

---

<a name="english"></a>
## English

**Persona Weaver** is a native extension for SillyTavern that uses AI to help create, refine, and manage User Personas, with automatic World Info synchronization.

This repository is the Vietnamese localization: the UI, prompts, and YAML templates are all in Vietnamese.

### ✨ Features

*   **AI Generation**: Automatically generate detailed, structured User Personas (YAML) based on simple prompts or templates.
*   **Smart Refinement & Diff View**: 
    *   Refine your persona with natural language instructions.
    *   **Smart Contrast**: Visually compare the original vs. refined text side-by-side, allowing you to selectively apply changes or edit directly.
*   **Drafts System**: Auto-save your generation history to the Drafts tab. Never lose an idea again.
*   **World Info Sync**: Automatically detects bound World Info books and allows one-click saving of your persona as an entry.
*   **Independent API**: Supports configuring a separate API (e.g., OpenAI, DeepSeek) for generation tasks, keeping your main chat context free.
*   **Mobile Friendly**: Optimized UI for touch screens and mobile devices.

### 📦 Installation

1.  **Prerequisite**: [TavernHelper (JS-Slash-Runner)](https://github.com/n0vi028/JS-Slash-Runner) is recommended for full World Info features.
2.  Open **Extensions** in SillyTavern.
3.  Click **Install Extension**.
4.  Paste the repo URL: `https://github.com/sisisisilviaxie-star/st-persona-weaver`
5.  Click **Save** and reload.

## 📄 License

MIT License
