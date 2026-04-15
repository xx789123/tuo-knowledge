# 前端部学习资料

> Vue3、React、TypeScript、前端工程化的完整知识库

## 官方文档

### Vue 3
- [Vue3官方文档(中文)](https://cn.vuejs.org/) - 官方中文文档
- [Vue3英文文档](https://vuejs.org/) - 最新英文文档
- [Vue 3 + TypeScript 2025企业架构](https://eastondev.com/blog/en/posts/dev/20251124-vue3-typescript-best-practices/) - 企业级Vue3架构指南
- [Vue 3 Best Practices 2025](https://expertdevelopers.in/blog/future-proof-your-frontend-5-vuejs-3-best-practices-for-2025-expert-developers) - 2025最佳实践
- [Vuetify](https://vuetifyjs.com/) - Material Design组件库
- [Pinia](https://pinia.vuejs.org/) - Vue3官方状态管理

### React
- [React新文档](https://react.dev/) - React官方最新文档
- [React TypeScript指南](https://react.dev/learn/typescript) - 官方TS教程
- [Next.js 15](https://nextjs.org/) - SSR框架
- [TanStack Query](https://tanstack.com/query/latest) - 数据请求状态管理

### TypeScript
- [TypeScript官方(中文)](https://www.typescriptlang.org/zh/) - 官方中文文档
- [Type Challenges](https://github.com/type-challenges/type-challenges) - 类型挑战练习
- [TypeScript 5.x新特性](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-5-0.html)

### 构建工具
- [Vite](https://cn.vitejs.dev/) - 下一代前端构建工具
- [Vitest](https://vitest.dev/) - Vite原生测试框架

## GitHub 热门开源项目

### Vue3 后台管理模板
- [vue-pinia-admin/pinx](https://github.com/vue-pinia-admin/pinx) - Vue3+Naive UI+Tailwind高级管理模板
- [hsl-git/soybean-admin](https://github.com/hsl-git/soybean-admin) - 美丽的Vue3+Naive UI管理模板
- [cmdparkour/vue-admin-box](https://github.com/cmdparkour/vue-admin-box) - vue3+element-plus后台管理
- [zclzone/v3-admin-vite](https://github.com/zclzone/v3-admin-vite) - Vue3+Vite+Element Plus模板
- [buqiyuan/vue3-antd-admin](https://github.com/buqiyuan/vue3-antd-admin) - Vue3+Ant Design Pro
- [framinus/peppa-admin](https://github.com/niaoge/peppa-admin) - Vue3+Element Plus管理后台

### React 后台管理模板
- [react-admin/react-admin](https://github.com/react-admin/react-admin) - React管理后台框架 (11k stars)
- [ant-design/pro-components](https://github.com/ant-design/pro-components) - Ant Design ProComponents
- [blitz-js/blitz](https://github.com/blitz-js/blitz) - React全栈框架
- [refinedev/refine](https://github.com/refinedev/refine) - React管理后台框架 (14k stars)

### Vue3 组件库
- [vuejs/awesome-vue](https://github.com/vuejs/awesome-vue) - Vue资源大合集 (42k stars)
- [sonicoder86/awesome-vue-3](https://github.com/sonicoder86/awesome-vue-3) - Vue3资源集合
- [struy-cn/awesome-vue-components](https://github.com/struy-cn/awesome-vue-components) - Vue3组件集锦
- [vueComponent/ant-design-vue](https://github.com/vueComponent/ant-design-vue) - Ant Design Vue (20k stars)

### React 组件库
- [shadcn/ui](https://github.com/shadcn-ui/ui) - copy-paste的React组件集
- [radix-ui/primitives](https://github.com/radix-ui/primitives) - 无样式React组件原语
- [chakra-ui/chakra-ui](https://github.com/chakra-ui/chakra-ui) - React组件库 (33k stars)
- [headlessui/headlessui](https://github.com/tailwindlabs/headlessui) - Tailwind无样式组件 (23k stars)

### 工具库
- [tanstack/query](https://github.com/tanstack/query) - React数据请求 (40k stars)
- [pinia-plugin-persistedstate/pinia-plugin-persistedstate](https://github.com/pinia-plugin-persistedstate/pinia-plugin-persistedstate) - Pinia持久化
- [vueuse/vueuse](https://github.com/vueuse/vueuse) - Vue组合式工具库 (22k stars)
- [sxlwar/vuer](https://github.com/sxlwar/vuer) - Vue3工具库

### 地图与可视化
- [apache/echarts](https://github.com/apache/echarts) - 百度图表库 (57k stars)
- [Leaflet/Leaflet](https://github.com/Leaflet/Leaflet) - 开源地图库 (32k stars)
- [visgl/react-map-gl](https://github.com/visgl/react-map-gl) - React地图组件
- [d3/d3](https://github.com/d3/d3) - 数据可视化 (109k stars)
- [Three.js](https://github.com/mrdoob/three.js) - 3D图形库 (94k stars)

## 核心技能

### 企业级Vue3项目结构
```
src/
├── api/                  # API封装
├── assets/              # 静态资源
├── components/          # 公共组件
├── composables/         # 组合式函数
├── router/             # 路由配置
├── stores/              # 状态管理(Pinia)
├── types/               # TypeScript类型
├── utils/               # 工具函数
└── views/               # 页面组件
```

### Pinia Store规范
```typescript
export const useUserStore = defineStore('user', () => {
  const token = ref<string>('')
  const userInfo = ref<UserInfo | null>(null)
  const isLoggedIn = computed(() => !!token.value)

  async function loginAction(credentials: LoginDTO) {
    const res = await login(credentials)
    token.value = res.token
    userInfo.value = res.user
  }

  return { token, userInfo, isLoggedIn, loginAction }
})
```

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

---
*由坨坨维护 · 2026-04-15 · 更新*
