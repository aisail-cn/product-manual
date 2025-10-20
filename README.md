# AI Network product manual

## 🧱 **字段说明文档**

### 🟦 **根字段**

| 字段名    | 类型     | 说明                                                         |
| --------- | -------- | ------------------------------------------------------------ |
| `version` | `string` | 当前产品说明书文档的版本号，方便比对与更新，例如 `"1.0.0"`。 |

---

### 🟦 `product`（产品基本信息）

| 子字段         | 类型                | 说明                                                             |
| -------------- | ------------------- | ---------------------------------------------------------------- |
| `id`           | `string`            | 产品唯一 ID（全局唯一），例如 `"AN-1001"`，建议与内部 SKU 对应。 |
| `name`         | `object`            | 产品名称，支持多语言，例如 `{ "zh": "...", "en": "..." }`。      |
| `model`        | `string`            | 产品型号，通常为市场型号，如 `"AN-R1000"`。                      |
| `brand`        | `string`            | 品牌名，如 `"AI Network"`。                                      |
| `category`     | `string`            | 产品类别（如 `Networking`、`Smart Home`）。                      |
| `release_date` | `string` (ISO 日期) | 产品正式发布时间，格式：`YYYY-MM-DD`。                           |

---

### 🟦 `meta`（文档元信息）

| 子字段         | 类型                     | 说明                                                                          |
| -------------- | ------------------------ | ----------------------------------------------------------------------------- |
| `language`     | `string`                 | 当前文档语言代码，如 `"zh"`, `"en"`, `"ja"`。                                 |
| `last_updated` | `string` (ISO 8601 时间) | 文档最近更新时间。                                                            |
| `author`       | `string`                 | 文档编写或维护人/团队名称。                                                   |
| `document_id`  | `string`                 | 文档唯一 ID（建议 = `manual-[product.id]-[lang]-v[version]`），用于版本追踪。 |

---

### 🟦 `overview`（产品概览）

| 子字段        | 类型            | 说明                                 |
| ------------- | --------------- | ------------------------------------ |
| `description` | `object`        | 产品简介，支持多语言。               |
| `features`    | `array[string]` | 产品主要特性（列表），建议简短有力。 |
| `images`      | `array[string]` | 产品外观、正面/背面等图片 URL。      |

---

### 🟦 `specifications`（技术规格）

| 子字段          | 类型            | 说明                                                            |
| --------------- | --------------- | --------------------------------------------------------------- |
| `hardware`      | `object`        | 硬件参数（CPU、内存、接口等）。                                 |
| ├ `cpu`         | `string`        | CPU 型号或描述                                                  |
| ├ `ram`         | `string`        | 内存配置                                                        |
| ├ `rom`         | `string`        | 存储配置                                                        |
| ├ `ports`       | `array[object]` | 接口信息，包含 `type`（WAN/LAN 等）、`quantity`、可选 `speed`。 |
| `wireless`      | `object`        | 无线参数。                                                      |
| ├ `standards`   | `array[string]` | 支持的无线标准，如 802.11ax                                     |
| ├ `bands`       | `array[object]` | 各频段信息，包含 `frequency` 和 `speed`。                       |
| `power`         | `object`        | 电源信息（输入/功耗）。                                         |
| ├ `input`       | `string`        | 供电输入，如 `"DC 12V / 2A"`                                    |
| ├ `consumption` | `string`        | 功耗描述                                                        |
| `dimensions`    | `object`        | 物理尺寸（mm）。                                                |
| ├ `width_mm`    | `number`        | 宽度                                                            |
| ├ `height_mm`   | `number`        | 高度                                                            |
| ├ `depth_mm`    | `number`        | 深度                                                            |
| `weight_g`      | `number`        | 重量，单位 g。                                                  |

---

### 🟦 `package_contents`（包装清单）

| 字段       | 类型     | 说明           |
| ---------- | -------- | -------------- |
| `item`     | `string` | 包装内物品名称 |
| `quantity` | `number` | 数量           |

---

### 🟦 `setup_instructions`（安装步骤）

| 子字段        | 类型     | 说明                              |
| ------------- | -------- | --------------------------------- |
| `step`        | `number` | 步骤编号（建议从 1 开始，整数）。 |
| `title`       | `string` | 步骤标题，简要说明要做什么。      |
| `description` | `string` | 详细说明，描述具体操作。          |
| `image`       | `string` | 对应步骤的图示（可选）。          |

---

### 🟦 `safety_notes`（安全注意事项）

| 类型            | 说明                       |
| --------------- | -------------------------- |
| `array[string]` | 各种安全提示、使用注意等。 |

---

### 🟦 `faq`（常见问题）

| 子字段     | 类型     | 说明           |
| ---------- | -------- | -------------- |
| `question` | `string` | 常见问题描述。 |
| `answer`   | `string` | 对应答案。     |

---

### 🟦 `warranty`（保修与售后）

| 子字段          | 类型     | 说明               |
| --------------- | -------- | ------------------ |
| `period_months` | `number` | 保修期（月）。     |
| `policy`        | `string` | 保修政策文字说明。 |
| `contact`       | `object` | 售后联系方式。     |
| ├ `phone`       | `string` | 电话               |
| ├ `email`       | `string` | 邮箱               |
| ├ `website`     | `string` | 售后网页链接       |

---

### 🟦 `extra_resources`（附加资源）

| 子字段                  | 类型     | 说明                    |
| ----------------------- | -------- | ----------------------- |
| `pdf_manual_url`        | `string` | PDF 说明书下载链接。    |
| `firmware_download_url` | `string` | 固件下载链接（如有）。  |
| `support_forum`         | `string` | 社区/论坛链接（如有）。 |

---

## 🧱 **可选扩展字段详细说明**

---

### 🟨 `related_products`（相关产品 / 配件 / 变体）

| 子字段          | 类型     | 说明                       |
| --------------- | -------- | -------------------------- |
| `id`            | `string` | 相关产品的唯一 ID          |
| `relation_type` | `string` | 与当前产品的关系类型，如： |

- `"accessory"`（配件）
- `"variant"`（同系列不同型号）
- `"optional_power_supply"`（可选电源）
- `"replacement_part"`（替换零件） |
  | `name` | `object` | 产品名称（支持多语言） |
  | `link` | `string` | 对应产品的 JSON 说明书文件 URL |

👉 用途：

- 前端可在说明书下方自动显示「相关产品 / 配件」区域
- 提供跳转链接，支持交叉引用

---

### 🟨 `regulatory`（法规与认证）

| 子字段           | 类型            | 说明                     |
| ---------------- | --------------- | ------------------------ |
| `certifications` | `array[object]` | 认证列表，每个对象包含： |

- `region`: 区域或认证类型（如 CE、FCC、CCC）
- `code`: 认证编号
- `issued_date`: 发证日期（`YYYY-MM-DD`） |
  | `standards_compliance` | `array[string]` | 符合的标准列表，如 RoHS、WEEE、ISO 等。 |
  | `warning_labels` | `array[string]` | 产品上的安全标签/警示语。 |

👉 用途：

- 方便导出报关资料、合规文档
- 前端可以自动渲染认证 Logo + 编号
- 对多区域销售尤为重要

---

### 🟨 `changelog`（版本更新记录）

| 子字段    | 类型            | 说明                 |
| --------- | --------------- | -------------------- |
| `version` | `string`        | 说明书版本号         |
| `date`    | `string`        | 该版本发布时间       |
| `changes` | `array[string]` | 本版本更新的内容摘要 |

👉 用途：

- 记录产品说明书的修改历史
- 前端可以在「版本信息」页展示更新日志
- 方便文档团队追踪变化

---

## 📌 **推荐文件组织方式（含扩展字段）**

```
/manuals/
  ├─ an1001/
  │   ├─ manual-an1001-zh-v1.0.0.json
  │   ├─ manual-an1001-en-v1.0.0.json
  │   ├─ manual-an1001-zh-v1.1.0.json
  │   └─ firmware/
  ├─ an1002/
  │   └─ manual-an1002-zh-v1.0.0.json
  └─ an-psu12v2a/
      └─ manual-an-psu12v2a-zh-v1.0.0.json
```

> 不同语言/版本用单独文件，而不是把多语言都塞在一个 JSON 里。
> 相关产品之间可以通过 `related_products` 相互链接。
