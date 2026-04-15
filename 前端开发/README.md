# 前端部学习资料

> Vue3、React、TypeScript、前端工程化的完整知识库

## 官方文档

### Vue 3
- [Vue3官方文档(中文)](https://cn.vuejs.org/) - 官方中文文档
- [Vue3英文文档](https://vuejs.org/) - 最新英文文档
- [Vue 3 + TypeScript 2025企业架构](https://eastondev.com/blog/en/posts/dev/20251124-vue3-typescript-best-practices/) - 企业级Vue3架构指南
- [Vue 3 Best Practices 2025](https://expertdevelopers.in/blog/future-proof-your-frontend-5-vuejs-3-best-practices-for-2025-expert-developers) - 2025最佳实践
- [Vue 3 Tutorial for Beginners 2025](https://themeselection.com/blog/vue-3-tutorial-for-beginners/) - 新手入门教程
- [Vuetify](https://vuetifyjs.com/) - Material Design组件库
- [Pinia](https://pinia.vuejs.org/) - Vue3官方状态管理
- [Vue Router 4](https://router.vuejs.org/zh/) - Vue3路由

### React
- [React新文档](https://react.dev/) - React官方最新文档
- [React TypeScript指南](https://react.dev/learn/typescript) - 官方TS教程
- [Next.js 15](https://nextjs.org/) - SSR框架
- [TanStack Query](https://tanstack.com/query/latest) - 数据请求状态管理
- [React Query](https://tanstack.com/query/v4) - v4版本

### TypeScript
- [TypeScript官方(中文)](https://www.typescriptlang.org/zh/) - 官方中文文档
- [TypeScript Deep Dive](https://basarat.gitbook.io/typescript/) - 深入理解TypeScript
- [Type Challenges](https://github.com/type-challenges/type-challenges) - 类型挑战练习
- [TypeScript 5.x新特性](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-5-0.html)

### 构建工具
- [Vite](https://cn.vitejs.dev/) - 下一代前端构建工具
- [Vite中文网](https://vitejs.cn/) - Vite中文文档
- [Webpack](https://webpack.js.org/) - 模块打包工具
- [Vitest](https://vitest.dev/) - Vite原生测试框架
- [esbuild](https://esbuild.github.io/) - Go编写的极快打包工具
- [Rollup](https://rollupjs.org/) - 库打包工具

### CSS框架
- [Tailwind CSS](https://tailwindcss.com/) - 实用优先CSS框架
- [UnoCSS](https://unocss.bootcss.com/) - 即时原子化CSS
- [PostCSS](https://postcss.org/) - CSS转换工具

### 地图与可视化
- [ECharts](https://echarts.apache.org/zh/) - 百度图表库
- [Leaflet](https://leafletjs.com/) - 开源地图库
- [Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js/) - 地图SDK
- [Three.js](https://threejs.org/) - 3D图形库
- [D3.js](https://d3js.org/) - 数据可视化

## 核心技能

### 企业级Vue3项目结构（推荐）
```
src/
├── api/                  # API封装
│   ├── modules/         # 按模块分
│   │   ├── user.ts
│   │   └── order.ts
│   └── index.ts
├── assets/              # 静态资源
│   ├── images/
│   └── styles/
├── components/          # 公共组件
│   ├── common/         # 通用组件
│   └── business/      # 业务组件
├── composables/        # 组合式函数
│   ├── useCount.ts
│   └── useUser.ts
├── config/             # 配置文件
├── constants/          # 常量定义
├── directives/         # 自定义指令
├── hooks/             # 生命周期钩子
├── layouts/           # 布局组件
├── router/            # 路由配置
│   └── index.ts
├── stores/             # 状态管理(Pinia)
│   ├── modules/
│   └── index.ts
├── types/              # TypeScript类型
│   ├── api.d.ts
│   └── global.d.ts
├── utils/              # 工具函数
│   ├── format.ts
│   └── validate.ts
└── views/              # 页面组件
    ├── Home/
    └── About/

环境变量：
VITE_API_BASE_URL=http://api.example.com
VITE_APP_TITLE=应用名称
```

### Pinia Store规范
```typescript
// stores/modules/user.ts
import { defineStore } from 'pinia'
import { ref, computed } from 'vue'
import { getUserInfo, login } from '@/api/modules/user'

export const useUserStore = defineStore('user', () => {
  // State
  const token = ref<string>('')
  const userInfo = ref<UserInfo | null>(null)

  // Getters
  const isLoggedIn = computed(() => !!token.value)
  const userName = computed(() => userInfo.value?.name ?? '')

  // Actions
  async function loginAction(credentials: LoginDTO) {
    const res = await login(credentials)
    token.value = res.token
    userInfo.value = res.user
  }

  return { token, userInfo, isLoggedIn, userName, loginAction }
})
```

### API封装规范
```typescript
// api/request.ts
import axios from 'axios'
import type { AxiosInstance, AxiosResponse } from 'axios'

const request: AxiosInstance = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL,
  timeout: 10000,
})

// 请求拦截器
request.interceptors.request.use(config => {
  const token = useUserStore().token
  if (token) config.headers.Authorization = `Bearer ${token}`
  return config
})

// 响应拦截器
request.interceptors.response.use(
  (response: AxiosResponse) => response.data,
  (error) => {
    if (error.response?.status === 401) {
      // 处理登录过期
    }
    return Promise.reject(error)
  }
)

export default request
```

### 前端性能优化
- [Web Vitals](https://web.dev/vitals/) - Google性能指标
- [Lighthouse](https://developer.chrome.com/docs/lighthouse/) - 性能审计
- [Bundle Analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) - 包大小分析
- [Code Splitting](https://vitejs.cn/guide/performance.html#路由懒加载) - 代码分割
- Tree Shaking配置
- 图片懒加载
- 组件懒加载

## 工具推荐

### 开发工具
- [VS Code](https://code.visualstudio.com/) - 首推编辑器
- [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) - Vue3 VSCode插件
- [TypeScript Vue Plugin](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) - TS支持

### 测试工具
- [Vitest](https://vitest.dev/) - Vite测试框架
- [Playwright](https://playwright.dev/) - E2E测试
- [Cypress](https://www.cypress.io/) - E2E测试

### 代码规范
- [ESLint](https://eslint.org/) - 代码检查
- [Prettier](https://prettier.io/) - 代码格式化
- [Husky](https://typicode.github.io/husky/) - Git hooks
- [lint-staged](https://github.com/lint-staged/lint-staged) - 暂存区检查

---
*由坨坨维护 · 2026-04-15 · 更新*
