# vue-router-control

作用于vue项目中, 路由控制方案, 包含对路由及单个按钮的权限控制。


## Install

```
npm install vue-router-control --save
```

## Usge

```javascript

import {filterAsyncRouter } from 'vue-router-control'

// 用户权限
const privilegesArr = ['556a8a6ce43609e0aca02830'];


// 页面所有路由
const router = [
  {
    path: "/",
    component: Demo,
    children: [
      {
        meta: { Privileges: ['556a8a6ce43609e0aca02830']},
        name: "react",
        component:'demo1',
        path: 'baidu/vue',
      },
      {
        meta: { Privileges: ['5b8394ed20078a6d47116a15']},
        name: "vue",
        component:'demo2',
        path: 'baidu/vue',
      },
      {
        meta: { Privileges: ['5c18a96aa2b00f64f5bff40b']},
        name: "augular",
        component:'demo3',
        path: 'baidu/vue',
      }
    ]
  },
  { path: '*', redirect: '/404', hidden: true }
]

console.log(filterAsyncRouter(router, privilegesArr)); // arguments1 页面所有路由 arguments2 用户权限内路由
```
## API

#### filterAsyncRouter
这个是用来过滤路由的，返回的是在这权限内的路由

#### hasOneOf
这个查询数组内的元素是否在里面，返回false和true