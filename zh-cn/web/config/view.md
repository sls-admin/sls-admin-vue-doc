# 视图配置
### 以demo模块视图配置为例进行解释
```shell
├── src                        // 源代码
│   ├── views                 // 视图
│       ├── index.js                 // 负责导出所有模块
│       ├──demo                 // demo模块视图
│           ├──index.js                // 负责导出该模块下所有的菜单
│           ├──article               // 左侧文章管理
│               ├──index.js               // 负责导出该菜单下的所有页面
│                   ├──list             // 文章列表页面
│                       ├──List.vue            // 文章列表组件
│                       ├──List.less           // 文章列表样式
│                       ├──List.js           // 文章列表js
│                       ├──index.js          // 负责导出文章列表组件
│       ├──other                 // 其他模块视图
```
通过上面的结构,views/index.js导出的视图结构实际上是这样:
```javascript
{
    Demo:{
        Article:{
            Edit:"文章编辑组件",
            List:"文章列表组件"
        }
    },
    Other:{}
    ......    
}
```
然后你就可以在路由的每个模块，配置路由对应组件时，通过``import {模块} from 'views/';`来引入模需要的视图模块。
> 需要注意的是
> 
> - 目录命名为小写，如果是多个单词，使用中横线隔开。
> - 文件名为大小，如果是多个单词，使用驼峰命名。
> - 文件名最好和上级目录名保持一致。