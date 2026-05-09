# Hướng dẫn kết nối đến Coder Workspace

Tài liệu này hướng dẫn bạn tất cả các phương pháp kết nối và làm việc với Coder Workspace của bạn, từ trình duyệt cho đến các phần mềm chuyên dụng.

> **Điều kiện tiên quyết:** Với các ứng dụng Desktop, bạn cần cài đặt Coder CLI và đăng nhập trên máy tính của mình trước.
> ```bash
> coder login http://localhost:9080
> ```

---

## 1. Trình duyệt (Web IDEs / Apps)
Các phương pháp nhanh nhất không cần cài đặt bất cứ thứ gì trên máy tính của bạn. Bạn chỉ cần vào Coder Web UI và click vào icon tương ứng trên Workspace:

* **code-server:** Cung cấp giao diện VS Code đầy đủ chạy trực tiếp trên tab trình duyệt.
* **Terminal:** Mở một giao diện SSH terminal chạy nền web.
* **JupyterLab / RStudio (nếu được setup):** Các IDE chuyên dụng cho Data Science chạy trên trình duyệt (tùy thuộc vào Coder template của bạn có cài sẵn hay không).

---

## 2. VS Code & Các IDE lõi VS Code (Cursor, Windsurf)
Phương pháp được khuyên dùng nhất cho các lập trình viên.

### Cách 1: Dùng Extension "Remote - SSH" (Khuyên dùng)
1. Mở terminal trên máy tính và chạy lệnh: `coder config-ssh`
2. Mở **VS Code**, cài đặt extension **Remote - SSH** (của Microsoft).
3. Nhấn `Ctrl + Shift + P` (hoặc `Cmd + Shift + P` trên Mac), chọn `Remote-SSH: Connect to Host...`
4. Chọn hostname của workspace từ danh sách (ví dụ: `main.personal.ttungbmt.coder`).

### Cách 2: Dùng Extension "Coder"
1. Mở **VS Code / Cursor / Windsurf**, cài extension **Coder**.
2. Nhấn vào biểu tượng Coder ở thanh công cụ bên trái.
3. Cấu hình URL của Coder server (`http://localhost:9080`) và đăng nhập.
4. Chọn workspace của bạn và nhấn biểu tượng thư mục để kết nối trực tiếp.

---

## 3. JetBrains IDEs (IntelliJ, PyCharm, GoLand, WebStorm...)
Coder hỗ trợ remote development cực kỳ tốt với các IDE của JetBrains thông qua JetBrains Gateway.

1. Tải và cài đặt phần mềm **JetBrains Gateway** (hoặc mở từ JetBrains Toolbox).
2. Cài đặt plugin **Coder** cho JetBrains Gateway.
3. Đăng nhập URL Coder của bạn.
4. Chọn Workspace, chọn IDE (ví dụ IntelliJ IDEA) muốn cài lên Workspace, và kết nối.

---

## 4. Coder Desktop (App bản địa)
**Coder Desktop** là một ứng dụng native do Coder cung cấp, hoạt động giống như một chiếc VPN cục bộ (tunnel) kết nối trực tiếp bạn với workspace.

1. Tải **Coder Desktop** từ trang chủ Coder.
2. Đăng nhập vào URL Coder của bạn.
3. Ứng dụng này sẽ tự động tạo kết nối ngầm (Coder Connect) giúp bạn dùng bất kỳ IDE hay phần mềm SSH nào trên máy tính mà không cần cấu hình phức tạp.

---

## 5. Terminal CLI (Coder SSH)
Cách dành cho các bạn thích gõ lệnh trực tiếp để vào server:

1. Mở terminal trên máy tính của bạn.
2. Gõ lệnh:
   ```bash
   coder ssh main.personal.ttungbmt
   ```
   *(Thay tên tương ứng bằng workspace của bạn).*

---

## 6. SSH Truyền thống & Các ứng dụng bên thứ 3 (Termius, MobaXterm, PuTTY...)

> **Lưu ý quan trọng:** Coder mặc định sử dụng cơ chế bảo mật Zero-Trust thông qua lệnh `ProxyCommand` để tạo đường hầm (tunnel). Các ứng dụng SSH bên thứ 3 (như Termius, PuTTY) **không hỗ trợ** đọc lệnh này từ file `~/.ssh/config`.

### Với các ứng dụng hỗ trợ OpenSSH (như Terminal mặc định của macOS/Linux)
Chạy lệnh `coder config-ssh` 1 lần, sau đó SSH bình thường:
```bash
ssh main.personal.ttungbmt.coder
```

### Với các ứng dụng KHÔNG hỗ trợ ProxyCommand (như Termius)
Mở một đường hầm (Local Port Forwarding) thủ công:
1. Bật Terminal chạy nền lệnh sau:
   ```bash
   coder port-forward main.personal.ttungbmt.coder --tcp 2222:22
   ```
2. Vào Coder Web UI -> **User Settings** -> **SSH Keys**. Dán Public Key của Termius vào đây.
3. Mở Termius, tạo Host mới:
   * **Address:** `127.0.0.1` | **Port:** `2222`
   * **Username:** `coder` | **SSH Key:** Chọn key tương ứng.