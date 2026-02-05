# AI 换衣应用实现计划

## 产品概述
一款时尚现代的 AI 虚拟换衣应用，用户上传人像照片后，从预设衣服库中选择衣服，AI 自动生成换衣效果图。

## 核心功能模块

### 1. 人像上传
- 拖拽或点击上传人像照片
- 实时预览上传的图片
- 支持 JPG/PNG 格式

### 2. 衣服选择
- 预设衣服库展示（上衣、连衣裙、外套等分类）
- 卡片式画廊布局
- 点击选择衣服，高亮显示选中状态

### 3. AI 换衣生成
- 一键生成换衣效果
- 显示处理进度
- 错误提示与重试

### 4. 结果展示
- 展示 AI 生成的换衣效果图
- 原图与效果图对比
- 下载结果图片
- 重新开始功能

## 设计风格
- **主题**: 深色科技感
- **配色**: 紫色+青色渐变为主色调
- **效果**: 玻璃态卡片、发光阴影、流畅动画

## 技术方案

### AI 服务
- 使用 Supabase Edge Function 作为 API 代理
- 调用 Replicate 平台的 IDM-VTON 模型
- 异步轮询获取生成结果

### 前端架构
- Zustand 管理应用状态
- React Query 处理 API 请求
- Framer Motion 实现动画

## 文件结构
```
src/
├── components/
│   ├── upload/
│   │   └── ImageUploader.tsx      # 图片上传组件
│   ├── wardrobe/
│   │   ├── ClothingGallery.tsx    # 衣服画廊
│   │   └── ClothingCard.tsx       # 衣服卡片
│   ├── result/
│   │   └── ResultDisplay.tsx      # 结果展示
│   └── common/
│       ├── StepIndicator.tsx      # 步骤指示器
│       └── LoadingOverlay.tsx     # 加载遮罩
├── stores/
│   └── appStore.ts                # Zustand 状态
├── services/
│   └── tryOnService.ts            # AI 换衣服务
├── data/
│   └── clothingData.ts            # 预设衣服数据
├── types/
│   └── index.ts                   # 类型定义
├── pages/
│   └── Index.tsx                  # 主页面（重写）
├── index.css                      # 设计系统（更新）
└── tailwind.config.ts             # Tailwind 配置（更新）
```

## 关键文件修改

| 文件 | 操作 | 说明 |
|------|------|------|
| `src/index.css` | 更新 | 添加深色主题 CSS 变量 |
| `tailwind.config.ts` | 更新 | 添加渐变、阴影配置 |
| `src/pages/Index.tsx` | 重写 | 主页面换衣应用界面 |
| `src/stores/appStore.ts` | 新建 | Zustand 状态管理 |
| `src/data/clothingData.ts` | 新建 | 预设衣服数据 |
| `src/types/index.ts` | 新建 | TypeScript 类型 |
| `src/components/*` | 新建 | 各功能组件 |
| `src/services/tryOnService.ts` | 新建 | AI 服务调用 |

## 实现步骤

### 阶段 1: 设计系统 (优先)
1. 更新 `index.css` 深色主题变量
2. 扩展 `tailwind.config.ts` 渐变和阴影
3. 创建类型定义

### 阶段 2: 核心组件
4. 创建 Zustand 状态管理
5. 实现图片上传组件
6. 实现衣服画廊组件
7. 创建预设衣服数据

### 阶段 3: 主页面
8. 重写 Index.tsx 主页面
9. 实现步骤指示器
10. 实现加载状态组件

### 阶段 4: AI 集成
11. 创建 AI 换衣服务（模拟模式）
12. 实现结果展示组件
13. 添加下载功能

## 验证方式
1. 运行 `pnpm run dev` 启动开发服务器
2. 访问应用首页，确认深色主题和渐变效果正常
3. 测试图片上传功能（拖拽和点击）
4. 测试衣服选择功能（分类切换、选中高亮）
5. 点击"开始换装"触发 AI 处理（初版为模拟效果）
6. 验证结果展示和下载功能
7. 测试响应式布局（移动端适配）

## 注意事项
- 首版使用模拟 AI 响应，后续集成真实 API
- 预设衣服使用 Unsplash 占位图
- 无需用户登录，匿名使用
