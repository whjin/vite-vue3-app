# Vue3 + Vite

## Node版本
> 20.9.0

### 配置vite.config.js 
```vite.config.js
export default defineConfig(({ mode }) => {
  return {
    base: mode == 'production' ? '/vue3-vite/' : './',
    plugins: [
      vue(),
    ],
    resolve: {
      alias: {
        '@': fileURLToPath(new URL('./src', import.meta.url))
      }
    }
  };
});
```

### 配置index.html
```html
<link rel="icon" href="/favicon.ico">

<script type="module" src="/src/main.js"></script>
```

### 一键提交部署
```shell
#!/usr/bin/env sh

# 发生错误时终止
set -e

# 构建
npm run build

# 提交main主分支
git add .
git commit -m "提交更新main分支"
git push origin main

# 进入dist文件夹
cd dist

# 提交gh-pages主分支
git add .
git commit -m "提交部署gh-pages分支"
git push origin gh-pages

# 退出
cd -
``
