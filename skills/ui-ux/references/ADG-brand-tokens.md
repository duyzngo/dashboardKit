# Token thương hiệu ADG (shadcn/ui + Tailwind v4)

Nguồn: ADG Core Design System (skill `adg-guidelines`). File này giữ phần token
dùng được cho màn hình web app. Tên token trùng tên biến của shadcn/ui, nên
Figma variable, CSS variable và class Tailwind dùng cùng một tên.

## 1. Quy tắc

- **Một màu chủ đạo: Brand `#0057A4`.** Không thêm màu nhấn thứ hai. Neutral là
  nền, chữ và viền. Màu status (success, warning, destructive) chỉ báo trạng
  thái hệ thống, không dùng để trang trí.
- **Font: Roboto** cho toàn bộ giao diện, Roboto Mono cho mã và dữ liệu kỹ thuật.
- **Tên token = tên biến shadcn.** Figma variable đặt đúng tên đó, không có `--`.
  Ví dụ: `primary-foreground` trong Figma ↔ `--primary-foreground` trong CSS ↔
  `text-primary-foreground` trong Tailwind.
- **Có dark mode** qua class `.dark` trên `<html>`, mặc định theo hệ điều hành (mục 2b).
  Nguồn ADG chưa có bảng màu tối, nên giá trị ở mục 2b là đề xuất cần ADG duyệt.

## 2. Token CSS (chép vào `globals.css`)

```css
@import "tailwindcss";

:root {
  /* Nền và chữ */
  --background: #FFFFFF;
  --foreground: #252627;
  --card: #FFFFFF;
  --card-foreground: #252627;
  --popover: #FFFFFF;
  --popover-foreground: #252627;

  /* Màu chủ đạo: Brand */
  --primary: #0057A4;
  --primary-hover: #003E8A;
  --primary-foreground: #FFFFFF;

  /* Phụ: nút xám, nền dịu */
  --secondary: #F4F5F6;
  --secondary-hover: #E8EBED;
  --secondary-foreground: #252627;
  --muted: #F4F5F6;
  --muted-foreground: #53575A;

  /* Nhấn nhẹ: hàng đang chọn, hover menu (cùng họ Brand, không phải màu mới) */
  --accent: #F2F7FB;
  --accent-foreground: #003E8A;

  /* Trạng thái hệ thống */
  --destructive: #A51712;
  --destructive-foreground: #FFFFFF;
  --success: #1F6F3D;
  --success-foreground: #FFFFFF;
  --warning: #705A00;
  --warning-foreground: #FFFFFF;

  /* Viền và focus */
  --border: #D6D9DC;
  --input: #8E9499;
  --ring: #0057A4;

  /* Biểu đồ: cùng họ Brand, phân biệt bằng độ đậm */
  --chart-1: #0057A4;
  --chart-2: #4585BD;
  --chart-3: #8AB2D5;
  --chart-4: #003E8A;
  --chart-5: #ADC9E2;

  /* Sidebar */
  --sidebar: #F4F5F6;
  --sidebar-foreground: #252627;
  --sidebar-primary: #0057A4;
  --sidebar-primary-foreground: #FFFFFF;
  --sidebar-accent: #F2F7FB;
  --sidebar-accent-foreground: #003E8A;
  --sidebar-border: #D6D9DC;
  --sidebar-ring: #0057A4;
}

/* Dark mode: đề xuất, xem mục 2b. Chỉ đổi giá trị, không đổi tên token. */
.dark {
  --background: #121212;
  --foreground: #F2F2F2;
  --card: #1E1E1E;
  --card-foreground: #F2F2F2;
  --popover: #262626;
  --popover-foreground: #F2F2F2;

  --primary: #0057A4;
  --primary-hover: #003E8A;
  --primary-foreground: #FFFFFF;

  --secondary: #2E2E2E;
  --secondary-hover: #383838;
  --secondary-foreground: #F2F2F2;
  --muted: #2E2E2E;
  --muted-foreground: #A3A3A3;

  --accent: #182A39;
  --accent-foreground: #8AB2D5;

  --destructive: #F1645F;
  --destructive-foreground: #121212;
  --success: #66D68F;
  --success-foreground: #121212;
  --warning: #E8BA02;
  --warning-foreground: #121212;

  --border: #333333;
  --input: #6B6B6B;
  --ring: #4585BD;

  --chart-1: #689BC9;
  --chart-2: #8AB2D5;
  --chart-3: #4585BD;
  --chart-4: #ADC9E2;
  --chart-5: #D0E0EE;

  --sidebar: #181818;
  --sidebar-foreground: #F2F2F2;
  --sidebar-primary: #0057A4;
  --sidebar-primary-foreground: #FFFFFF;
  --sidebar-accent: #182A39;
  --sidebar-accent-foreground: #8AB2D5;
  --sidebar-border: #333333;
  --sidebar-ring: #4585BD;

  color-scheme: dark;
}

:root {
  color-scheme: light;
}

@theme inline {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-card-foreground: var(--card-foreground);
  --color-popover: var(--popover);
  --color-popover-foreground: var(--popover-foreground);
  --color-primary: var(--primary);
  --color-primary-hover: var(--primary-hover);
  --color-primary-foreground: var(--primary-foreground);
  --color-secondary: var(--secondary);
  --color-secondary-hover: var(--secondary-hover);
  --color-secondary-foreground: var(--secondary-foreground);
  --color-muted: var(--muted);
  --color-muted-foreground: var(--muted-foreground);
  --color-accent: var(--accent);
  --color-accent-foreground: var(--accent-foreground);
  --color-destructive: var(--destructive);
  --color-destructive-foreground: var(--destructive-foreground);
  --color-success: var(--success);
  --color-success-foreground: var(--success-foreground);
  --color-warning: var(--warning);
  --color-warning-foreground: var(--warning-foreground);
  --color-border: var(--border);
  --color-input: var(--input);
  --color-ring: var(--ring);
  --color-chart-1: var(--chart-1);
  --color-chart-2: var(--chart-2);
  --color-chart-3: var(--chart-3);
  --color-chart-4: var(--chart-4);
  --color-chart-5: var(--chart-5);
  --color-sidebar: var(--sidebar);
  --color-sidebar-foreground: var(--sidebar-foreground);
  --color-sidebar-primary: var(--sidebar-primary);
  --color-sidebar-primary-foreground: var(--sidebar-primary-foreground);
  --color-sidebar-accent: var(--sidebar-accent);
  --color-sidebar-accent-foreground: var(--sidebar-accent-foreground);
  --color-sidebar-border: var(--sidebar-border);
  --color-sidebar-ring: var(--sidebar-ring);

  /* Bo góc theo thang ADG: 4, 8, 16, 24, full */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;
  --radius-xl: 24px;
  --radius-full: 9999px;

  --font-sans: "Roboto", system-ui, sans-serif;
  --font-mono: "Roboto Mono", ui-monospace, monospace;
}
```

## 2b. Dark mode

**Cơ chế.** Tailwind v4 khai biến thể bằng `@custom-variant dark (&:where(.dark, .dark *));`.
Mặc định theo hệ điều hành (`prefers-color-scheme`), người dùng chọn Sáng / Tối /
Hệ thống trong Cài đặt → Giao diện. Không có nút xoay vòng, không tự đổi theo giờ.
Thư viện `next-themes` dùng `attribute="class"`, `defaultTheme="system"`,
`enableSystem`, `disableTransitionOnChange`, `suppressHydrationWarning` trên `<html>`.

**Quy tắc cho component.** Không viết `dark:` trong component. Mọi màu đi qua token,
đổi theme chỉ cần đổi khối `.dark`. Thư viện ngoài (Sonner, Dialog) đọc token nên
đổi theo tự động.

**Thứ tự bề mặt ở nền tối.** Chìm < trang < card < popover, mỗi bậc sáng hơn bậc
dưới khoảng 3–5 đơn vị L. Vùng tô (nút phụ, hàng đang chọn, ô nhập, hover) là lớp
phủ sáng hơn card, không tối hơn. Ở nền sáng thì ngược lại.

**Viền.** Đường chia dùng `border` `#333333` (trang trí, không cần 3:1). Viền ô
nhập và điều khiển dùng `input` `#6B6B6B`, đạt 3:1 trên card. Không bỏ viền ô
nhập ở nền tối.

**Màu chữ đứng trên màu token.** Mỗi `--X-foreground` đi cùng `--X` ở cả hai theme.
Nút primary giữ màu `#0057A4` với chữ trắng (7.2:1) ở cả hai theme, không sáng lên.
Trạng thái (`destructive`, `success`, `warning`) sáng lên khi làm chữ trên nền tối,
chữ trên nút đảo sang tối để giữ tương phản.

**Accent ở nền tối.** Hàng đang chọn dùng `#182A39` (tint Brand ~20% trên nền tối)
với chữ `#8AB2D5`, không dùng `#F2F7FB` của bản sáng.

**Bóng.** Popover và modal ở nền tối dùng vòng viền 1px `#3D3D3D` cộng bóng đậm hơn
bản sáng. Không bóng màu, không gradient trang trí.

**Vùng luôn sáng** (ví dụ trang chia sẻ): đặt class `force-light` ở khung ngoài, khai
lại toàn bộ token của `:root` trong class đó.

**Độ tương phản đã đo (xấp xỉ, theo WCAG):**

| Cặp | Tỉ lệ | Đạt |
| --- | ---: | --- |
| `foreground` `#F2F2F2` trên `card` `#1E1E1E` | 15:1 | AA |
| `muted-foreground` `#A3A3A3` trên `card` | 6.6:1 | AA |
| `muted-foreground` `#A3A3A3` trên `secondary` `#2E2E2E` | 5.4:1 | AA |
| `primary-foreground` `#FFFFFF` trên `primary` `#0057A4` | 7.2:1 | AA |
| `destructive` `#F1645F` trên `card` (chữ) | 5.3:1 | AA |
| `destructive-foreground` `#121212` trên `destructive` `#F1645F` | 6.0:1 | AA |
| `accent-foreground` `#8AB2D5` trên `accent` `#182A39` | 6.6:1 | AA |
| `input` `#6B6B6B` trên `card` `#1E1E1E` | 3.1:1 | 3:1 UI |
| `ring` `#4585BD` trên `background` `#121212` | 4.8:1 | 3:1 UI |
| `success` `#66D68F` trên `card` (chữ) | 9:1 | AA |
| `warning` `#E8BA02` trên `card` (chữ) | 9:1 | AA |

## 3. Chữ và độ tương phản

| Vai trò | Token | Tỉ lệ với nền trắng |
| --- | --- | --- |
| Chữ chính | `foreground` `#252627` | 15:1 |
| Chữ phụ, nhãn, mô tả | `muted-foreground` `#53575A` | 7.5:1 |
| Chữ trên nút chính | `primary-foreground` `#FFFFFF` trên `primary` `#0057A4` | 7.2:1 |
| Chữ báo lỗi | `destructive` `#A51712` | 7.7:1 |

**Không dùng Tertiary `#8E9499` cho chữ.** Trên nền trắng chỉ đạt khoảng 3.1:1, trượt
AA cho chữ nhỏ. Tertiary chỉ dùng cho icon trang trí hoặc chữ rất lớn.

**Viền ô nhập dùng `input` `#8E9499`, không dùng `border` `#D6D9DC`.** Viền nhạt
chỉ khoảng 1.4:1 trên nền trắng, không đủ để thấy ô nhập (WCAG 1.4.11 yêu cầu 3:1).
`border` `#D6D9DC` vẫn dùng cho đường chia, viền card, viền bảng.

## 4. Chữ (Roboto)

| Vai trò ADG | Class Tailwind | Cỡ | Độ đậm |
| --- | --- | --- | --- |
| Display | `text-3xl font-semibold` | 30px | 600 |
| H1 | `text-2xl font-semibold` | 24px | 600 |
| H2 | `text-xl font-semibold` | 20px | 600 |
| H3 | `text-lg font-semibold` | 18px | 600 |
| Body strong | `text-sm font-medium` | 14px | 500 |
| Body | `text-sm` | 14px | 400 |
| Data | `text-sm font-medium tabular-nums` | 14px | 500 |
| Label | `text-xs font-medium` | 12px | 500 |
| Caption | `text-xs` | 12px | 400 |

Nguồn ghi cỡ theo pt cho bản in và mobile. Bảng trên là quy đổi sang px của
Tailwind cho web app và giữ cặp độ đậm của nguồn. Đây là phần cần xác nhận với
ADG.

## 5. Khoảng cách, bo góc, viền, bóng

- **Khoảng cách**: dùng thang mặc định của Tailwind. Các giá trị ADG (2, 4, 6, 8, 12,
  16, 24, 32, 48, 64, 96, 160 px) đều có trong thang: `0.5`, `1`, `1.5`, `2`, `3`,
  `4`, `6`, `8`, `12`, `16`, `24`, `40`. Không dùng giá trị ngoài danh sách này.
- **Bo góc**: `rounded-sm` 4px, `rounded-md` 8px (nút, ô nhập), `rounded-lg` 16px
  (card), `rounded-xl` 24px, `rounded-full` (chip, avatar).
- **Viền**: 1px. **Ring focus**: 2px, màu `ring` `#0057A4`.
- **Bóng**: nguồn có bậc 1, 4, 8, 16 px. Popover dùng bậc 4, modal dùng bậc 8.
  Nguồn không định nghĩa blur, nên tạm dùng `shadow-md` của Tailwind, cần xác nhận.
- **Icon**: `size-4` (16px) trong nút và ô nhập, `size-6` (24px) cho icon độc lập.

## 6. Thành phần shadcn/ui cần chỉnh token

Dùng nguyên component shadcn/ui, chỉ sửa các chỗ sau để khớp ADG:

- **Button**: variant `default` dùng `bg-primary hover:bg-primary-hover text-primary-foreground`
  (shadcn mặc định là `hover:bg-primary/90`). Variant `destructive` dùng
  `bg-destructive text-destructive-foreground`. Variant `outline` dùng viền `border-input`.
- **Card**: `rounded-xl` → `rounded-lg` (16px). Viền `border-border`.
- **Input, Textarea, Select**: viền `border-input`. Focus `ring-2 ring-ring`.
- **Badge**: variant `default` dùng `primary`. Trạng thái dùng `success`, `warning`,
  `destructive`. Xem mục 7 về nền tint.
- **Switch, Checkbox, Radio**: trạng thái bật dùng `primary`, viền khi tắt dùng `input`.
- **Tabs, Sidebar, DropdownMenu**: mục đang chọn dùng `accent` và `accent-foreground`.
- **Table**: đường chia `border`, hàng hover dùng `muted`.
- **Dialog, Sheet, Popover**: nền `popover`, bóng theo mục 5.
- **Progress**: rãnh `secondary`, thanh `primary`.
- **Skeleton**: `muted`.
- **Avatar**: nền `muted`, chữ `muted-foreground`.
- **Alert**: dùng `destructive`, `success`, `warning` cho biến thể trạng thái.
- **Sonner (toast)**: nền `popover`, viền `border`.

Các component còn lại (Accordion, Breadcrumb, Tooltip, Form, Command, Pagination)
dùng token mặc định của shadcn, không cần chỉnh thêm.

## 7. Chưa có trong nguồn, cần xác nhận

- **Nền tint cho trạng thái** (ví dụ nền xanh nhạt cho badge thành công). Nguồn
  chỉ có màu chữ và màu đặc. Hiện badge dùng nền đặc hoặc viền. Cần bảng
  `Green/Yellow/Red` đầy đủ từ `references/adg-color-tokens.md` của nguồn.
- **Giá trị dark mode (mục 2b) là đề xuất.** Nguồn ADG chưa có bảng màu tối. Cần ADG
  duyệt, đặc biệt là nền `#121212` và xám trung tính (không dùng navy như dự án
  tham chiếu), và màu `primary-hover` `#003E8A` ở nền tối (tối hơn nền nên đọc như
  nhấn xuống).
- **Bóng có blur.** Nguồn chỉ có offset.
- **Cỡ chữ cho web.** Bảng mục 4 là quy đổi, chưa phải số của ADG.
