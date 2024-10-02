# less

## vite+ts 无法识别 less 文件

#### 离奇报错 vite 本身是具有 less 解析的不需要安装 less-loader

#### 只需要安装 less webpack 才需要安装 less-loader 如若出现可尝试以下方案

#### 在 vite.config.ts 文件中配置 less

```vite
  css:{
        preprocessorOptions:{
            less:{
                modifyVars: {
                    //引入less基础变量
                    hack: `true; @import (reference) "${path.resolve("src/assets/css/index.less")}";`,
                },

                javascriptEnabled: true,
            }
        }
    }
```
