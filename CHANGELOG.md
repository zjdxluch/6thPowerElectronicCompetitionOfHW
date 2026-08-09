# 第六届华为大学生电力电子创新大赛 - 网页变更日志

## 2026-07-31 版本变更记录

### 当前版本: index.html

---

### 修改内容

#### 1. 新增"赛事介绍"视图
- 创建新视图 `view-intro`，包含"赛题介绍"和"赛事旅程"两个卡片
- 从 `view-agenda` 移除这两个卡片
- 页面加载默认显示"赛事介绍"视图

#### 2. 底部导航重构
- 从3个Tab扩展为4个Tab
- 新增"赛事介绍"按钮（使用 `info` 图标）
- 导航顺序：赛事介绍 → 参赛指南 → 活动地图 → 照片直播

#### 3. 参赛指南新增"赛题介绍"卡片
- 标题：赛题介绍
- 图标：zap（闪电）
- 边框颜色：border-l-green-300
- 内容：
  ```
  赛题一：三端口功率变换器设计
  导向：以高密高效、暂态高过载光储功率变换为核心，鼓励拓扑、工艺和算法创新。
  ```

#### 4. 行程安排Tab优化
- 按钮尺寸调整：`px-5 py-2.5` → `px-4 py-2`
- 间距调整：`gap-2` → `gap-1.5`
- 移除负边距 `-mx-1`
- 添加 `snap-x` 和 `snap-start` 实现滚动对齐

#### 5. 行程安排滚动指示器
- 添加左右箭头 `‹ ›`（闪烁动画提示可滚动）
- 添加小圆点指示器显示当前位置
- 箭头会根据滚动位置动态显示/隐藏
- 修复右箭头ID错误（arrow-left → arrow-right）

#### 6. CSS新增样式
```css
.snap-x { scroll-snap-type: x mandatory; }
.snap-start { scroll-snap-align: start; }
@keyframes pulse-arrow {
  0%, 100% { opacity: 0.4; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.15); }
}
.arrow-pulse { animation: pulse-arrow 1.2s ease-in-out infinite; }
```

---

### 页面结构

```
底部导航
├── 赛事介绍 (view-intro)
│   ├── 赛题介绍
│   └── 赛事旅程
├── 参赛指南 (view-agenda)
│   ├── 赛题介绍（新增）
│   ├── 行程安排（Tab切换 + 箭头指示器 + 小圆点）
│   ├── 答辩议程
│   ├── 酒店信息
│   ├── 车辆接送
│   ├── 天气预报
│   └── 温馨提醒
├── 活动地图 (view-map)
│   ├── 布局图
│   └── 游戏卡片列表
└── 照片直播 (view-album)
    ├── 相册跳转链接
    └── 二维码
```

---

### 备份文件
- `archive/index.original.bak` - 原始版本备份

---

### 技术栈
- HTML5 单页应用
- Tailwind CSS（CDN引入）
- Lucide Icons 图标库
- Vanilla JavaScript

---

### 备注
- 行程安排Tab在小屏设备上支持左右滑动
- 滑动时有箭头闪烁提示和滚动指示器
- 默认选中"赛事介绍"视图
- 行程安排默认选中8月15日
