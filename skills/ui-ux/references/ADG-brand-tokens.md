Name: ui-ux-remake

Description: Làm lại màn hoặc bộ màn đã có trên canvas Figma cho sản phẩm ADG, theo hai hướng: giữ brand của file gốc, hoặc chuyển về gu và token ADG. Dựng bằng component shadcn/ui, biến và text style đặt tên trùng code. Dùng khi người dùng nói làm lại, dựng lại, redesign, remake, refresh màn, giữ brand, theo gu skill, chuẩn hoá theo ADG. Không dùng để soi lỗi hay thêm vài chi tiết nhỏ.

Instructions:

## Nền tảng (áp dụng cho mọi việc)

Bạn làm việc trên canvas Figma cho ADG. Không viết code. Mục tiêu: file Figma để dev dựng lại bằng shadcn/ui mà không phải đặt lại tên hay đoán màu.

**Thương hiệu ADG**
- Một màu chủ đạo: primary `#0057A4`, hover `#003E8A`. Không thêm màu nhấn thứ hai.
- Neutral (nền, chữ, viền) là phần còn lại của giao diện.
- Destructive, success, warning chỉ báo trạng thái hệ thống. Không dùng để trang trí.
- Font Roboto cho mọi chữ. Roboto Mono cho mã, ID, số liệu kỹ thuật.

**Biến (variables): tên trùng biến CSS của shadcn, không có tiền tố `--`**

Collection "Color" có hai mode, Light và Dark. Giá trị theo thứ tự Light / Dark:
- background: #FFFFFF / #121212
- foreground: #252627 / #F2F2F2
- card: #FFFFFF / #1E1E1E
- card-foreground: #252627 / #F2F2F2
- popover: #FFFFFF / #262626
- popover-foreground: #252627 / #F2F2F2
- primary: #0057A4 / #0057A4
- primary-hover: #003E8A / #003E8A
- primary-foreground: #FFFFFF / #FFFFFF
- secondary: #F4F5F6 / #2E2E2E
- secondary-hover: #E8EBED / #383838
- secondary-foreground: #252627 / #F2F2F2
- muted: #F4F5F6 / #2E2E2E
- muted-foreground: #53575A / #A3A3A3
- accent: #F2F7FB / #182A39
- accent-foreground: #003E8A / #8AB2D5
- destructive: #A51712 / #F1645F
- destructive-foreground: #FFFFFF / #121212
- success: #1F6F3D / #66D68F
- success-foreground: #FFFFFF / #121212
- warning: #705A00 / #E8BA02
- warning-foreground: #FFFFFF / #121212
- border: #D6D9DC / #333333
- input: #8E9499 / #6B6B6B
- ring: #0057A4 / #4585BD
- chart-1: #0057A4 / #689BC9
- chart-2: #4585BD / #8AB2D5
- chart-3: #8AB2D5 / #4585BD
- chart-4: #003E8A / #ADC9E2
- chart-5: #ADC9E2 / #D0E0EE
- sidebar: #F4F5F6 / #181818
- sidebar-foreground: #252627 / #F2F2F2
- sidebar-primary: #0057A4 / #0057A4
- sidebar-primary-foreground: #FFFFFF / #FFFFFF
- sidebar-accent: #F2F7FB / #182A39
- sidebar-accent-foreground: #003E8A / #8AB2D5
- sidebar-border: #D6D9DC / #333333
- sidebar-ring: #0057A4 / #4585BD

Collection "Radius": sm 4, md 8, lg 16, xl 24, full 9999.
Collection "Spacing" (px): 0, 2, 4, 6, 8, 12, 16, 24, 32, 48, 64, 96, 160. Không dùng số ngoài danh sách này.

**Text styles: tên theo class Tailwind, cỡ theo px**
- text-3xl font-semibold: 30 / 600
- text-2xl font-semibold: 24 / 600
- text-xl font-semibold: 20 / 600
- text-lg font-semibold: 18 / 600
- text-sm font-medium: 14 / 500
- text-sm: 14 / 400
- text-xs font-medium: 12 / 500
- text-xs: 12 / 400

Quy tắc: không gõ hex vào layer. Mọi màu, bo góc, khoảng cách, cỡ chữ đều gắn biến hoặc text style. Không detach instance.

**Component: tên và props trùng shadcn/ui**

Dùng component shadcn có sẵn trong file hoặc thư viện shadcn của Figma. Nếu chưa có thì tạo đúng tên và props sau:
- Button: variant (default, secondary, outline, ghost, destructive, link), size (default, sm, lg, icon).
- Input, Textarea, Select, Checkbox, Switch, Badge, Tabs, Table, Dialog, Sheet, DropdownMenu, Popover, Tooltip, Avatar, Alert, Progress, Skeleton, Breadcrumb, Accordion, Sidebar, Sonner (toast), Form (nhãn, ô nhập, câu lỗi).
- Card gồm các phần: CardHeader, CardTitle, CardDescription, CardContent, CardFooter.
- Empty state: đặt tên Empty.

Trạng thái là variant với các giá trị: default, hover, focus, disabled. Thêm loading, error, empty khi component cần.

**Chỉnh so với shadcn mặc định (ADG)**
- Button variant default là primary: nền `primary`, chữ `primary-foreground`. Trong mỗi khu chỉ đặt một nút default.
- Button outline: viền `input`, nền `background`. Hover chỉ đổi nền sang `secondary-hover`, viền giữ nguyên.
- Button destructive: nền `destructive`, chữ `destructive-foreground`.
- Bo góc: Button và Input dùng `md`. Card dùng `lg`. Badge và Avatar dùng `full`.
- Chiều cao nút và ô nhập: 40 px trên desktop, 44 px trên mobile.
- Input và Select: viền `input`. Focus có viền `ring` 2 px.
- Card trong trang không có bóng. Bóng chỉ cho Dropdown, Popover, Dialog.
- Không vẽ vòng focus cho nút, link, tab, checkbox, card. Vòng focus chỉ cho ô nhập và ô chọn.

**Bố cục**
- Web desktop: rộng 1440. App có sidebar: rộng 256, nội dung padding 24.
- Mobile: rộng 375, padding 16.
- Gap lưới 12. Padding card 20 trên desktop, 16 trên mobile.
- Auto layout cho mọi frame có nội dung. Absolute chỉ cho lớp phủ.

**Nội dung**
- Tiếng Việt có đủ dấu nếu sản phẩm tiếng Việt. Nhãn nút là động từ và đối tượng.
- Không lorem ipsum. Không emoji trong giao diện. Icon dùng Lucide, cùng một bộ.

**Cấm**
Gradient trang trí, hiệu ứng kính mờ, glow, bóng màu, viền đứt (trừ vùng tải tệp và ô trống), hero chiếm cả màn, chữ màu trên nền cùng màu.

**Dark mode**
Thiết kế Light trước. Dark chỉ đổi mode của biến, không chỉnh màu tay trên layer.

**Đặt tên và annotation (dev-ready)**
- Frame màn: `{Màn}/{breakpoint}`. Annotation ghi tên biến và component, không ghi hex.
- Điểm logic chưa chốt: viết dạng câu hỏi trong annotation, không tự quyết.

**Khi không đọc được file**
Nếu không đọc được biến, component hoặc không chụp được frame: dừng, nói rõ thiếu quyền gì, nhờ người dùng chọn frame hoặc gửi ảnh. Không đoán token.

## Lối này: làm lại màn đã có

**Chọn hướng**
- "Giữ brand", "giữ màu", "giữ font": giữ màu và font của file gốc. Dựng lại biến từ màu gốc, đặt tên theo shadcn. Bố cục giữ nguyên, trừ khi người dùng nói đổi bố cục.
- "Theo gu skill", "theo ADG", "chuẩn hoá": chuyển về biến và text style ADG ở phần nền tảng.
- Không nói rõ: hỏi một câu với hai lựa chọn. Không tự chọn.

**Quy tắc giữ**
- Không sửa frame gốc. Nhân bản thành `{Màn}/before` và giữ nguyên.
- Giữ nội dung và luồng: cùng nhãn, cùng số liệu, cùng hành động. Chỉ đổi cách dựng, trừ khi người dùng yêu cầu đổi bố cục.
- Thay khối tự vẽ bằng component shadcn tương ứng. Ghi vào annotation: tên cũ → component mới.

**Quy trình**
1. Nhân bản frame gốc thành `before`. Không sửa nó nữa.
2. Kiểm kê: liệt kê các khối trên màn, mỗi khối là component shadcn nào, hoặc cần tạo mới.
3. Lập kế hoạch dạng bảng ngắn: việc giữ, việc đổi, việc thêm (trạng thái còn thiếu). Phân mức 🔴, 🟠, 🟡 như lối soi lỗi.
4. Dừng và hỏi người dùng duyệt kế hoạch. Đây là cổng duy nhất của lối này.
5. Dựng `after` theo kế hoạch đã duyệt, cùng breakpoint với `before`. Dùng auto layout, biến và text style.
6. So sánh `before` và `after` cạnh nhau. Ghi những chỗ khác nhau có chủ đích, và những chỗ không chủ đích. Chỗ không chủ đích phải sửa trước khi báo.
7. Báo theo năm mục chuẩn.

**Kiểm riêng cho làm lại**
- Nội dung không mất: đếm số nhãn, số nút, số trường ở `before` và `after`, phải khớp hoặc có lý do.
- Hành động chính vẫn là một và vẫn nằm đúng chỗ, trừ khi người dùng yêu cầu đổi.
- Trạng thái rỗng, lỗi, đang tải được giữ hoặc bổ sung, không bị bỏ.
- Màu của `after` chỉ đến từ biến, không có hex lẻ.

## Báo khi giao (năm mục)
1. Frame `before` và `after`, cùng breakpoint.
2. Hướng đã chọn: giữ brand hay theo ADG.
3. Biến và component đã dùng; chỗ chưa gắn biến.
4. Phần chưa làm hoặc giữ nguyên có chủ đích.
5. Điểm cần người duyệt.
