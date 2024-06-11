# Add Vconsole 

## 安装vconsole
```Shell
npm install vconsole vite-plugin-vconsole -D
```

## 修改vite.config.js
- 引入库
```html
import { viteVConsole } from 'vite-plugin-vconsole'
```

- 配置plugin
```html

    viteVConsole({
      entry: path.resolve('src/main.js'), // 入口文件，或者可以使用这个配置: [path.resolve('src/main.ts')]
      localEnabled: false, // 本地是否启用
      enabled: mode === 'test', // 是否启用
      config: {
        maxLogNumber: 1000,
        theme: 'dark' // 主题颜色
      }
    })
```

## 修改main.js
- 引入vconsole
```html
import Vconsole from 'vconsole'
```

- 修改代码
```html
createApp(App).use(new Vconsole()).mount('#app')
```


