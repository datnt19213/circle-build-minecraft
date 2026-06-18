# Minecraft Circle Builder

[Tiếng Việt](#tiếng-việt) | [English](#english)

---

## Tiếng Việt

Công cụ web giúp tính toán và trực quan hóa cách xây vòng tròn/ellipse trong Minecraft theo từng bước, hiển thị theo lưới block và chunk border. Chạy hoàn toàn offline, không cần server — chỉ 1 file HTML duy nhất.

### Cách dùng

Mở file `minecraft-circle-builder.html` bằng bất kỳ trình duyệt nào (Chrome, Edge, Firefox...). Không cần cài đặt gì thêm.

### Tính năng

#### Kích thước
- Nhập radius theo **block** hoặc **chunk** (1 chunk = 16 block), tự convert qua lại
- Radius X và Z độc lập (dựng được hình ellipse), có toggle đồng bộ X = Z
- Khung viền nét đứt hiển thị đúng kích thước vùng xây, tự snap theo chunk nếu đang chọn đơn vị chunk

#### 3 chế độ vẽ
| Mode | Mô tả |
|---|---|
| **Thin** | Viền tròn mỏng 1 block |
| **Thick** | Viền dày, tùy chỉnh độ dày (số block) |
| **Filled** | Lấp đầy toàn bộ bên trong |

#### Build theo step
- Vòng tròn được chia theo góc (sector) thành nhiều bước xây
- Tự tính số bước theo **số bước mong muốn** hoặc **số block/bước mục tiêu** — đổi kích thước hoặc mode sẽ tự chia lại
- Click vào từng step để xem riêng, đánh dấu "đã xây" (xanh), bước đang chọn (cam)
- Điều hướng bằng nút Prev/Next hoặc phím `←` `→`, phím `Space` để xem toàn bộ

#### Hiển thị canvas
- Lưới block, chunk border 16×16 (có label tọa độ chunk), tâm điểm, tọa độ từng block
- Toggle bật/tắt từng lớp hiển thị độc lập
- **Zoom tự do** bằng cuộn chuột hoặc nút +/− — giới hạn min/max tự tính theo kích thước hiện tại (min: nhìn thấy toàn vùng chunk, max: nhìn thấy đúng 1 chunk)
- **Pan** bằng kéo chuột hoặc chạm (touch)
- Nút "Fit to view" (phím `f`) để tự căn giữa và zoom vừa khung hình

#### Thống kê
- Tổng số block, kích thước diameter, số chunk bị ảnh hưởng
- Số block của step hiện tại
- **Số stack cần dùng** (tùy chỉnh kích thước stack, mặc định 64) kèm chi tiết số stack đầy / dư

#### Xuất dữ liệu Minecraft
- Tùy chỉnh vật liệu block và Y level
- Xem trước lệnh `/setblock` (Java Edition)
- Copy toàn bộ lệnh vào clipboard
- Xuất file `.txt` chứa tọa độ, chia theo từng step

#### Giao diện
- **Theme sáng/tối**, tự nhớ lựa chọn lần sau (lưu trong `localStorage`)
- **Đóng/mở sidebar** mà không mất state đang thiết lập (chỉ ẩn bằng hiệu ứng, không gỡ khỏi DOM)
- Font Roboto / Roboto Mono, icon Lucide-style, animation bằng GSAP

### Phím tắt

| Phím | Chức năng |
|---|---|
| `←` / `a` | Step trước |
| `→` / `d` | Step sau |
| `Space` | Xem tất cả (bỏ chọn step) |
| `+` / `=` | Zoom in |
| `-` | Zoom out |
| `f` | Fit to view |
| `b` | Đóng/mở sidebar |
| `t` | Đổi theme sáng/tối |

### Công nghệ

HTML + CSS thuần (biến CSS theo kiểu shadcn) + JavaScript thuần, Canvas API để vẽ, [GSAP](https://gsap.com) cho animation. Không phụ thuộc framework hay build step nào.

### Đề xuất mở rộng (chưa làm)

- Xuất lệnh cho Bedrock Edition (`/fill`)
- Mode hình trụ nhiều tầng Y (xây tường có chiều cao)
- Tô màu block theo vật liệu khác nhau từng lớp
- Lưu/load preset cấu hình qua URL hoặc file JSON

---

## English

A web-based utility tool to calculate and visualize Minecraft circle/ellipse construction step-by-step, featuring a block grid and chunk borders. Runs completely offline with zero server dependencies — just a single HTML file.

### Usage

Open the `minecraft-circle-builder.html` file using any modern web browser (Chrome, Edge, Firefox...). No installation or configuration required.

### Features

#### Dimensions & Sizing
- Input radius in either **blocks** or **chunks** (1 chunk = 16 blocks) with automatic conversion.
- Independent X and Z radii (for drawing ellipses) with a toggle to sync X = Z.
- Dashed bounding box indicating exact build boundaries, auto-snapping to chunk lines when chunk unit is active.

#### 3 Drawing Modes
| Mode | Description |
|---|---|
| **Thin** | 1-block thick outline circle |
| **Thick** | Customized thick outline (specify block width) |
| **Filled** | Fully filled solid circle/ellipse |

#### Step-by-Step Construction
- Divides the circle into multiple build steps based on sectors (angles).
- Auto-calculates steps based on **desired total steps** or **target blocks per step** — automatically recalculates on resize or mode switch.
- Interactive steps: Click to isolate, marks completed steps (Green) and active step (Orange).
- Seamless navigation using Prev/Next buttons or keyboard arrows `←` `→`, press `Space` to reset view to all steps.

#### Canvas & Rendering
- Complete block grid, 16×16 chunk borders (with chunk coordinate labels), center point indicator, and individual block coordinates.
- Independent toggles to show/hide any rendering layer.
- **Infinite Zooming**: Scroll wheel or `+`/`-` keys — dynamically constrained bounding box (min: fits entire chunk region, max: zooms into exactly 1 chunk).
- **Smooth Panning**: Click-and-drag or touch controls.
- "Fit to view" shortcut (press `f`) to instantly re-center and adapt zoom level.

#### Analytics & Statistics
- Total block count, diameter calculation, and total affected chunks.
- Block counter specialized for the current selected step.
- **Stack Calculator**: Custom stack sizes (defaults to 64) breakdown showcasing full stacks and leftover items.

#### Minecraft Command Exporter
- Customizable block material and Y-level configuration.
- Real-time `/setblock` command generator preview (Java Edition).
- Fast copy-to-clipboard functionality.
- Export raw text file (`.txt`) with absolute coordinates categorized by steps.

#### User Interface
- **Dark / Light Theme** toggle with persistent storage saved inside `localStorage`.
- **Collapsible Sidebar**: Hides gracefully via animations without tearing down the DOM state.
- Styled using Roboto / Roboto Mono typography, Lucide-styled icons, and smooth transitions powered by GSAP.

### Keybindings

| Key | Function |
|---|---|
| `←` / `a` | Previous Step |
| `→` / `d` | Next Step |
| `Space` | Clear selection (View all) |
| `+` / `=` | Zoom In |
| `-` | Zoom Out |
| `f` | Fit to View |
| `b` | Toggle Sidebar |
| `t` | Toggle Light/Dark Theme |

### Tech Stack

Pure HTML, vanilla CSS (utilizing Shadcn-style variables), vanilla JavaScript, Canvas API for ultra-fast grid rendering, and [GSAP](https://gsap.com) for fluid layout animations. Zero dependencies, zero compilation steps.

### Planned Enhancements

- Bedrock Edition command exporter (`/fill`).
- Cylindrical mode (multi-layered Y level walls).
- Multi-material layering (different block definitions per layer).
- Save/Load configuration presets via URL query strings or local JSON files.
