# TOEIC AI Masterclass (Phan Gia An)

**TOEIC AI Masterclass** là một ứng dụng web Single-Page Application (SPA) thông minh, được thiết kế để tự động tạo đề thi TOEIC (Part 5, 6, 7) và đóng vai trò như một "Siêu Trí Tuệ AI - Giáo Viên Kèm Riêng". Hệ thống không chỉ cung cấp bài tập mà còn đi sâu vào phân tích ngữ pháp, từ vựng và vạch trần các bẫy ETS một cách chi tiết bằng tiếng Việt.

Dự án được viết hoàn toàn bằng **HTML, Tailwind CSS và Vanilla JavaScript**, hoạt động hoàn toàn ở phía client (trình duyệt) mà không cần cài đặt server phức tạp. Hệ thống gọi trực tiếp đến API của Google Gemini và Groq.

---

## 🚀 Tính năng nổi bật

### 1. Sinh Đề Tự Động (AI Exam Generation)
- **Hỗ trợ 3 dạng bài TOEIC chính**: 
  - **Part 5**: Incomplete Sentences (Câu đơn độc lập).
  - **Part 6**: Text Completion (Điền từ vào đoạn văn).
  - **Part 7**: Reading Comprehension (Đọc hiểu văn bản).
- **Tuỳ biến quy mô**: Chọn luyện tập chế độ "Mini" (nhỏ, tải nhanh) hoặc "Chuẩn TOEIC" (full).
- Sử dụng mô hình AI mạnh mẽ (`Gemini 3.1 Flash Lite` hoặc `GPT-OSS 120B` qua Groq) để tạo ra các bộ đề đa dạng, bám sát cấu trúc đề thi thật của ETS.

### 2. Giáo Viên AI Kèm Riêng (Teacher Analyzer Engine)
- **Chấm điểm & Giải thích ngay lập tức**: Vừa chọn đáp án xong, AI sẽ vạch trần bản chất của cả đáp án đúng và sai.
- **Mổ xẻ cấu trúc câu**: Phân tích cú pháp chi tiết [S] (Chủ ngữ), [V] (Động từ), [O] (Tân ngữ), [M] (Thành phần bổ trợ).
- **Dịch nghĩa**: Cung cấp bản dịch tiếng Việt mượt mà cho câu hỏi và đoạn văn.
- **Vạch trần Bẫy TOEIC**: Cảnh báo các bẫy đồng âm, bẫy từ vựng hay bẫy cấu trúc mà người ra đề hay dùng.
- **Hệ Sinh Thái Từ Vựng**: Mở rộng họ từ (Word Family), các cụm từ (Collocation) và từ đồng nghĩa/trái nghĩa (Áp dụng riêng cho Part 5).
- **Giảng Giải Sâu**: Nút yêu cầu AI giải thích cặn kẽ hơn nếu học viên vẫn chưa hiểu bài.

### 3. Hỏi Đáp Trực Tiếp Với AI (Interactive Chatbot)
- Tích hợp một chatbot thu nhỏ ngay dưới mỗi câu hỏi.
- Cho phép người dùng trực tiếp đặt câu hỏi vặn vẹo lại Giáo viên AI về cấu trúc, từ vựng hoặc thắc mắc cá nhân đối với câu hỏi hiện tại.

### 4. Công Cụ Hỗ Trợ Làm Bài
- **Bút dạ quang (Highlighter)**: Tô đậm văn bản trong bài đọc (Part 6, 7) với 3 màu (Vàng, Xanh, Hồng) giúp đánh dấu keyword dễ dàng.
- **Tải HTML**: Xuất và tải bài test về máy dưới dạng HTML để ôn tập offline.
- **Dark/Light Mode**: Giao diện chuyển đổi Sáng/Tối mượt mà, thân thiện với mắt người học.
- **Responsive Layout**: Hoạt động mượt mà và hiển thị xuất sắc trên cả màn hình máy tính lẫn thiết bị di động.

---

## 🛠 Cài đặt và Sử dụng

Vì dự án là một file HTML tĩnh, bạn **không cần cài đặt Node.js hay bất kì server nào**.

1. **Clone repository về máy:**
   ```bash
   git clone <repo_url>
   ```
2. **Mở tệp HTML:**
   Nhấp đúp chuột vào file `index.html` để mở trực tiếp trên trình duyệt (Chrome, Edge, Safari,...).
3. **Cấu hình API Key:**
   - Để ứng dụng hoạt động, bạn cần cung cấp API Key.
   - Bấm vào biểu tượng **Chìa khóa (Key)** ở góc phải trên cùng màn hình.
   - Chọn loại AI bạn muốn sử dụng (Gemini hoặc Groq) và nhấp vào "Lấy API Key" để đi đến trang cung cấp (Hoàn toàn miễn phí).
   - Nhập Key vào ô và bấm **Lưu**. 
   - Ứng dụng hỗ trợ lưu trữ nhiều Key cùng lúc (tự động xoay vòng để tránh lỗi giới hạn - Rate Limit).

---

## 💻 Kiến trúc & Công nghệ (Tech Stack)

- **Frontend:** HTML5, CSS3.
- **Styling:** [Tailwind CSS](https://tailwindcss.com/) (Import qua CDN).
- **Icons:** [FontAwesome 6](https://fontawesome.com/) (Import qua CDN).
- **Logic & API calls:** Vanilla JavaScript (`fetch` API xử lý REST requests).
- **Storage:** `localStorage` để lưu trữ trạng thái người dùng (API Keys, Theme, Mô hình AI đang chọn, v.v.).

---

## ⚠️ Lưu ý về API Rate Limit
- Việc sinh đoạn văn dài (Part 6, 7) tốn rất nhiều tài nguyên của mô hình AI.
- Nếu gặp lỗi quá tải (`429 Too Many Requests`), hệ thống đã được lập trình sẵn để **tự động chờ và thử lại** (Auto-Retry). Bạn có thể cấu hình nhập nhiều API Key vào mục cấu hình để hệ thống san sẻ dung lượng, giúp sinh đề nhanh và mượt mà hơn.

---

## 👤 Tác giả
**Thiết kế và Phát triển bởi: Phan Gia An**
Dự án được tinh chỉnh và phát triển thông qua phương pháp lập trình AI-assisted.