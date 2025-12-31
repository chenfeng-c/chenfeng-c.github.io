# IconFont 集成指南

## 使用步骤

### 1. 访问 IconFont
打开 https://www.iconfont.cn/ 并登录或注册账号

### 2. 创建图标项目
1. 点击"资源管理" → "我的项目"
2. 点击"新建项目"
3. 填写项目信息：
   - 项目名称：心流科技官网
   - 前缀：icon
   - FontClass/Symbol：选择 FontClass
4. 点击确定

### 3. 添加图标到项目
1. 搜索你需要的图标（如：创新、团队、服务、客户、质量、优化）
2. 点击图标添加到购物车
3. 点击购物车图标，选择"添加至项目"
4. 选择刚才创建的项目

### 4. 获取在线链接
1. 进入项目页面
2. 点击"Font class"标签
3. 点击"生成在线链接"
4. 复制生成的链接（格式如：`//at.alicdn.com/t/c/font_xxxxxx.css`）

### 5. 集成到项目
1. 打开 `index.html` 文件
2. 找到注释 `<!-- IconFont 图标链接 - 请替换为你的 iconfont.cn 项目链接 -->`
3. 在下方添加你的链接，例如：

```html
<link rel="stylesheet" href="//at.alicdn.com/t/c/font_xxxxxx.css">
```

### 6. 使用图标

#### 方式一：使用 IconFont 组件（推荐）
```vue
<template>
  <IconFont iconClass="icon-innovation" :size="24" color="#0066CC" />
</template>

<script>
import IconFont from '@/components/IconFont.vue'

export default {
  components: {
    IconFont
  }
}
</script>
```

#### 方式二：直接使用类名
```vue
<template>
  <i class="iconfont icon-innovation"></i>
</template>
```

## 图标映射表

| 当前组件 | IconFont 类名 | 建议图标 |
|---------|--------------|---------|
| IconInnovation | icon-innovation | 灯泡、创意 |
| IconTeam | icon-team | 团队、用户组 |
| IconService | icon-service | 服务、客服 |
| IconCustomer | icon-customer | 客户、用户 |
| IconQuality | icon-quality | 质量认证、奖杯 |
| IconOptimization | icon-optimization | 优化、设置 |

## 替换现有图标

1. 在 `Home.vue` 等文件中，将原有的图标组件替换为：

```vue
<!-- 旧代码 -->
<IconInnovation />

<!-- 新代码 -->
<IconFont iconClass="icon-innovation" :size="40" color="#0066CC" />
```

2. 根据需要调整 `size` 和 `color` 属性

## 注意事项

- 确保图标类名与 IconFont 项目中的类名一致
- 链接必须包含 `//` 开头，不要添加 `https:`
- 建议定期检查并更新图标库，以获得最新图标