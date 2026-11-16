# Bộ Lạc Thời Tiền Sử (Prehistoric Tribes) - Web Port HTML5

Dự án chuyển đổi nguyên bản từ game J2ME nổi tiếng **Bộ Lạc Thời Tiền Sử** (Bản mod V5 F3 240x320) sang nền tảng Web hiện đại bằng **TypeScript, Vite và HTML5 Canvas 2D**.

---

## 🌟 Mục Tiêu Dự Án
- **Port trung thực tuyệt đối:** Giữ nguyên vẹn 100% đồ họa pixel-art, âm thanh MIDI, dữ liệu bản đồ, cốt truyện tiếng Việt và hệ thống gameplay.
- **Không giả lập (No Emulator):** Ứng dụng chạy trực tiếp trên trình duyệt web thuần Canvas 2D, không phụ thuộc máy ảo J2ME/Java Runtime.
- **Đa nền tảng:** Chơi mượt mà trên trình duyệt PC (bàn phím / numpad) và điện thoại di động (bàn phím ảo D-Pad cảm ứng).

---

## 📁 Cấu Trúc Dự Án

```text
prehistoric-tribes-web/
├── docs/                      # Tài liệu phân tích và kiến trúc
│   ├── ASSET_FORMATS.md       # Quy cách giải mã nhị phân pd0, a, sa, ma, pi*
│   ├── FEATURE_MATRIX.md      # Ma trận tính năng đối chiếu
│   ├── GAME_STATE_SCHEMA.md   # Cấu trúc lưu trữ game state
│   ├── PARITY_ISSUES.md       # Theo dõi khác biệt kỹ thuật và xử lý
│   ├── PORT_PLAN.md           # Lộ trình triển khai theo các cổng nghiệm thu
│   ├── SYMBOL_MAP.md          # Bảng đối chiếu deobfuscation các lớp Java
│   └── TEST_BASELINE.md       # Báo cáo mã băm, checksums và thông số chuẩn
├── research/                  # Dữ liệu nghiên cứu đối chiếu
│   ├── original/              # File JAR và extracted gốc (read-only)
│   ├── java-decompiled/       # 17 lớp Java đã decompile
│   └── javap/                 # Bytecode dump disassembled đối chiếu
├── tools/
│   └── extract-all-assets.py  # Pipeline trích xuất toàn bộ assets tự động
├── public/assets/             # 97 Assets đã trích xuất & chuẩn hóa
│   ├── atlas/                 # Terrain atlas pixel (terrain.png 1024x178)
│   ├── data/                  # pd0_tables.json, a_tables.json, binary plans
│   ├── locales/vi.json        # Bản địa hóa Tiếng Việt (229 UI, 72 mô tả, 236 truyện)
│   ├── maps/                  # 17 màn chơi chiến dịch (level_00 đến level_16)
│   ├── music/                 # 5 bản nhạc MIDI gốc (track_0.mid đến track_4.mid)
│   ├── splash/                # Màn hình boot l0.png, l1.png, l2.png
│   └── textures/              # 45 PNGs đóng gói (pi0, pi8, pi9) & standalone
├── src/                       # Mã nguồn game TypeScript
│   ├── content/               # TextBank tiếng Việt
│   ├── core/                  # GameClock (fixed timestep), AssetLoader
│   ├── debug/                 # SpriteInspectorScene (soi sprite, zoom 1x/2x/4x)
│   ├── platform/              # Canvas, InputManager, AudioPlayer, Persistence
│   ├── render/                # J2MEGraphics (Adapter javax.microedition.lcdui.Graphics)
│   ├── scenes/                # BootScene, MenuScene, GameScene, SceneManager
│   └── world/                 # TileMap renderer
├── tests/                     # Kiểm thử tự động Vitest
│   └── unit/                  # Unit tests cho adapter, input, textbank
├── index.html                 # Giao diện web & khung điện thoại giả lập
├── package.json
├── tsconfig.json
└── vite.config.ts
```

---

## 🚀 Hướng Dẫn Cài Đặt & Chạy Game

### Yêu Cầu Hệ Thống
- Node.js (khuyến nghị v18+)
- Trình duyệt Chrome / Edge / Safari / Firefox hiện đại

### Cài Đặt Thư Viện
```bash
cd prehistoric-tribes-web
npm install
```

### Chạy Môi Trường Phát Triển (Dev Server)
```bash
npm run dev
```
Mở trình duyệt tại: `http://localhost:3000`

### Chạy Kiểm Thử Tự Động (Tests)
```bash
npm test
```

### Đóng Gói Bản Phát Hành (Production Build)
```bash
npm run build
```
Kết quả xuất ra thư mục tĩnh `dist/`, sẵn sàng triển khai trên bất kỳ Web Server / Hosting nào (Vercel, Netlify, Cloudflare Pages, VPS).

---

## 🎮 Hướng Dẫn Điều Khiển

| Thao Tác | Phím PC | Bàn Phím Ảo Điện Thoại |
|---|---|---|
| **Di chuyển con trỏ** | Mũi tên (▲ ▼ ◄ ►) / WASD / Numpad 8, 2, 4, 6 | Phím điều hướng D-Pad |
| **Chọn / Thực hiện** | Enter / Space / Phím 5 | Nút 5 (Select / OK) |
| **Phím mềm Trái** | F1 / Q (Keycode -6) | L-Soft |
| **Phím mềm Phải** | F2 / E / Esc (Keycode -7) | R-Soft |
| **Phóng to màn hình** | Nút `Scale: 1x / 2x / 3x` | Tự động thích ứng |
| **Soi Sprite & Assets** | Nút `🔍 Sprite Inspector` | Nút trên thanh công cụ |
"# bolacthoitiensu" 
