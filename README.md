## EasyDoc是什么
- WHAT：EasyDoc是一个`易配置的降本提效的项目文档系统`
- WHY：
    - 减低复杂项目的`上手难度`，提升用户体验
    - 抹平项目组新老人员`信息差`
    - 将项目的业务细节载体从`开发者`变更为`文档工具`
- HOW：通过流程`用户引导`、流程`操作手册`、页面`说明文档`、`项目说明`文档、`关键点注解`文档等方式实现
- 现状：EasyDoc已经在微医集团内部孵化一年多了，已经接入了十几个线上应用，正在集团内部全面推广中。同时向社区开源推广，`希望能给社区带来一点新鲜的血液`，期待大家的使用接入，有任何问题欢迎留言评论、或在github给我们提意见。
- 典型场景：管理后台、复杂表单、复杂流程、复杂交互😉😉
- 不适场景：大屏项目、游戏类项目🤣🤣

## EasyDoc起源
### 先来看看一个故事


![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7dac1ad19fc34e87a6d8e166a2e232fb~tplv-k3u1fbpfcp-watermark.image?)

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/56868b4292ff403091056c392b24e5d5~tplv-k3u1fbpfcp-watermark.image?)

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/973f43a666c8482384d1e1e2dcb36345~tplv-k3u1fbpfcp-watermark.image?)

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b3e3119dbf78403dbfe97a9b12fdff0c~tplv-k3u1fbpfcp-watermark.image?)

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d13db6b9c58a425287bbf3301c39eb17~tplv-k3u1fbpfcp-watermark.image?)

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4a1e88ea2cdc449f9fa07f6547f24371~tplv-k3u1fbpfcp-watermark.image?)

### 由上面的故事可以得出项目研发过程中的一些文档相关问题：
- 完整业务逻辑分散在原型图、bug系统、代码注释、人脑记忆中，不易检索、容易丢失，`给项目的持续迭代带来了极大的可维护性成本`
- 长期迭代开发的项目，只有开发者知道业务细节，新人根本接手不了。一旦开发或产品离职，业务逻辑随之丢失，交接文档根本无法起到太大作用。`给项目研发带了极大的可控性风险`
- 外部的操作手册PDF，由于重视程度不够、项目迭代频繁，总是`忘记及时更新`，沦为鸡肋。
- 即使有健全的文档，在流程具体的操作过程中也会遇到很多问题。`用户体验很不好，并且要时常对用户或运营进行培训和24小时问题解答`。如果有实时的用户引导或操作手册就好了。
others
- 只有粗略的项目背景介绍，没有页面介绍或模块介绍
- 没有用户引导或用户引导不统一，用法怪异，用户体验差
- 有操作文档，但多系统跳转的复杂操作无能为力
- 无人维护业务文档或维护成本过高
### 针对上述问题设计解决方案
- `项目文档`：
    - 首次：在页面被第一次打开时弹窗向用户`介绍一次当前系统的背景、目标、功能、注意事项`
    - 更新：通过版本号控制的方式在实现项目文档更新重新弹窗一次
    - 回看：后续如果需要继续翻看文档可通过点击右上角EasyDoc按钮查看
- `页面文档`：
    - 打开：点击右上角EasyDoc按钮才显示，`弹窗查看当前页面的功能介绍`和`使用注意事项`等
    - 更新：通过更新对应页面的json文件更新
- `页面关键点文档`：
    - 打开：点击右上角EasyDoc按钮才显示，`对页面某个关键的逻辑点做注解备注`，方便用户或开发理解
    - 更新：通过更新对应页面的json文件更新
- `可编辑节点文档`：
    - 打开：点击右上角EasyDoc按钮才显示，用于解决：'用户前台系统展示数据，后台系统编辑展示的数据的架构模式中，解决运营不知道去哪里修改前台展示内容的场景'
    - 更新：通过更新对应页面的json文件更新
- `用户引导`：
    - 打开：调用EasyDoc的api进行操作，`复杂流程使用用户引导进行傻瓜式教学`，并结合步骤关键点文档进行注解加强理解
    - 更新：前端开发维护
- `操作手册`：
    - 打开：点击右上角EasyDoc按钮打开，`对多页面或多系统跳转的极复杂流程进行步骤化注解`，让用户在页面上`实时实地实景`的看对应的操作手册，跟随操作手册一步步操作。
    - 更新：通过更新项目的操作文档json文件更新
## EasyDoc视频使用演示
[EasyDoc哔哩哔哩演示视频](https://www.bilibili.com/medialist/play/473288250?from=space&business=space_series&business_id=548384&desc=1&spm_id_from=333.999.0.0)

## EasyDoc技术选型变化及迭代
- 版本1 typesciprt+rollup+less+jest
    
    为了打包更小我们没有使用任何UI框架并使用rollup，没错，我们就是一群追求极致的年轻人😎😎，但这导致我们使用js编写html的时候吃尽了苦头ε=(´ο｀*)))唉。为了可维护性更好我们决定使用typescript，这确实提高了我们的代码质量，更重要的是使我们意识到代码质量的重要性。`我们使用jest框架编写单元测试，这的确消耗了我们一些时间，但对于一个没有专职测试人员的架构项目，这样做非常有必要`。单元测试极大的提高了自研项目的健壮性、可维护性、可用性、稳定性。
- 版本2 typescript+rollup+less+jest+vue2

    是的，我们使用vue2重构了js编写dom的代码，这不是因为`vdom可以给我们带来性能的提升，这点性能对于现代浏览器来说根本不是瓶颈`。主要是因为js编写dom的可维护性太低了😂😂，这也让我们深刻的体会到了三大框架对于前端开发的意义。
 
 - 版本3 vue3+ts+element-plus开发可视化配置json插件(副包、暂未开源)
 
     我们发现由前端在public里编写项目的json文件的交互形式对前端同学确实不太友好，这无疑将业务文档的维护工作全权交给了前端同学。当时我们是这样考虑的🤔🤔：

     `多年来前端由于不直接接触业务方和数据源，导致前端人员在项目组中充当开发资源没有地位没有思考没有发言权没有业务成长没有晋升机会；我们希望前端通过承担EasyDoc维护项目业务文档的方式来贴近、掌握、思考、反哺业务，提高前端在项目组中的地位和发言权，通过前端视角带给项目更多的价值增长。`
     
     然而当我们去推广的时候，发现这种方式有一些弊端：1.产品、测试、后端同学没有前端代码权限没办法修改文档。2.前端维护全部文档的工作可能过重。3.部分前端并不想贴近业务也不需要贴近业务而我们不能强人所难。所以我们开发了可视化配置json文件的插件来解决这个问题。

- 版本4 lerna

    为了加速首屏渲染，我们尽可能的减小主包的大小，所以我们拆分了一些副包，这让我们的代码仓库过多。目前的开发人员稳定所以没什么影响，但`开发人员频繁调整带来的仓库管理负担的隐患我们必须未雨绸缪提前解决😜😜`。于是我们使用lerna将所有EasyDoc相关的代码聚合到一起，并统一管理授权和部署npm的工作。

## EasyDoc技术实现方案思考过程
- 技术需求：我们需要给项目、页面、某个标签添加一段文字备注
- 技术诉求：我们需要建立强力的div和业务文档json的一一对应关系
- 解决方案1：使用博客网站常用的Xpath方案实现
    - 优点是对页面源码没有入侵性；文档和项目代码完全解耦；任何人都可以编辑修改非常方便
    - 缺点是`如果页面源码修改了会导致Xpath失效需要重新添加，而且那些失效了也不知道，对于频繁迭代的项目来说维护文档简直就是灾难🤣🤣`
- 解决方案2：使用vue指令+element tooltip做一个文档插件
    - 优点是dom借用了element能力不需要额外开发，文档就近存储在vue html里面非常简便利于理解和修改
    - 缺点是`只能前端维护文档，太依赖vue和element通用性差，文档侵入性太强`
- 解决方案3：使用标签自定义属性docId建立标签和json文档的映射关系
    - 优点是`对源码入侵小，文档和源码解耦放在项目public文件夹里，后期通过可视化插件让所有人都能够轻松的编辑修改🤞🤞`
    - 缺点是没有完全将文档和项目解耦；需要给标签添加docId还是有弱入侵性
- 集体讨论后决定使用解决方案3实现
## 通过docId建立html标签和json文档映射关系方案
![easydoc json (1).png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2a8a62b0a90e429c9b6469dcd9b419c0~tplv-k3u1fbpfcp-watermark.image?)
## EasyDoc代码组织架构图

![EasyDoc架构图.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6efea6a2d116469f8f25cfcd3f973e83~tplv-k3u1fbpfcp-watermark.image?)

## 架构自研项目推广迭代
- `✨试点运行很重要`

    一个架构自研项目在上线之前是无法预测用户态度的，这个时候试点项目就非常有必要和价值了。`通过试点项目观测产品的稳定性、易用性、用户使用姿势、用户学习成本等，可以在正式推广之后减少很多的风险和不确定性😊😊`。

- 产品发布会

    通过一场正式的演讲来向全公司推广架构项目是一个非常好的途径，既能够有时间充分的讲述你的产品，又能够利用会议录屏回看功能来持续推广。还能和同学们现场进行思维的碰撞，收集同学们的思路灵感和意见来完善产品。`不要害怕别人battle你，这是完善自身的一种非常有效的方式`。

- 寻找潜在用户，好产品也要好推销
    
    `机会不会主动来找你，你要主动去找机会`。多和其他业务线的产品、前端、测试、后台聊聊业务文档的事情，倾听他们的吐槽、了解他们的痛点、共情他们的痛苦，顺势推出我们的产品并演示，趁热打铁拿下他；如果不能当天拿下，也要记录在案来日回访。
    
- `✨倾听用户的声音，不要反驳要及时响应`

    `用户并不在乎开发的技术实现细节和开发问题开发难点，用户只在意自己的痛点和什么时候能解决🤦‍♂️🤦‍♂️`。不要反驳用户的使用姿势、思维方式不对，而是应该引导他或者迁就他的方式。你要知道：用户就是个只会嗷嗷叫的孩子他啥都不会，而我们的使命是让他用我们的产品用的舒服而不是用的嗷嗷叫。
    - 故事1：我们去找某个产品推广EasyDoc希望她能接入，她听完介绍后也觉得很好，但是回复业务太忙了，没有工期写文档接入。后来该产品的运营一直吐槽产品难用不会用，产品教的焦头烂额，想起了我们。`自从接入了EasyDoc后，产品反馈流程问题吐槽、咨询少了一大半🤦‍♀️🤦‍♀️，沟通成本骤降了很多，用户体验非常好`。自此之后她成了我们的忠实用户。
    - 故事2：EasyDoc右上角弹窗原先是hover状态下就会弹出的，同时很多应用用户名点击退出登录也在右上角，很容易误划到EasyDoc面板。我们跟用户解释为什么要做成hover弹窗出现？是为了节约用户点击的这一步骤，这是用户体验优化。但`用户并不关心我们的优化点，用户只关心误划问题🤷‍♀️🤷‍♀️`，当我们意识到我们的优化确实给用户带来了副作用时，我们决定去掉优化改成点击才弹窗。
    - 故事3：EasyDoc原本是弹窗后固定在右边的，同时很多后台系统的页面都有表格，表格操作按钮也在右边，所以我们的面板挡住了用户操作按钮，需要用户来回点击开关EasyDoc面板。这很不人性化，我们意识到了这个问题，并准备下个版本优化掉。但用户3天内多次询问我们什么时候改好，我们回复和其他优化一起在下个版本迭代掉。但`在用户眼里，我们改个小问题太慢了而且用户并不关心其他的优化🤷‍♂️🤷‍♂️`。当我们意识到这点后，在第3天晚上单独把这个需求拎出来修改发布掉了。
    - 故事4：EasyDoc操作手册原本是各自独立的，因为每个操作手册都是独立的模块单元。但是用户觉得应该可以一个接一个的看，或者彼此跳转看，甚至不同系统间的操作手册也可以关联起来跳转。`我们非常想反驳用户你的使用姿势真是奇葩！简直是异想天开瞎搞乱搞🙌🙌。但是我们很有素质，我们认真考虑了用户诉求，重新定义了操作手册的操作方式满足了用户的痛点。用户真可爱`。
- 用户的使用痛点就是迭代的目标和价值

    `软件即服务，用户的痛点就是价值点`，闭门造车是很难造出好产品的。
## EasyDoc使用教程

### 1. 安装依赖

```
npm i we-easydoc --save
```

### 2. 初始化参数

```javascript
// 使用默认参数
import EasyDoc from 'we-easydoc'
import 'we-easydoc/lib/index.css'
EasyDoc.init()

// 自定义参数
EasyDoc.init({
  urlPrefix: "/easy-doc",
  easyDocPath: "/public/easy-doc/EasyDoc.json",
  easyManualsPath: "/public/easy-doc/Manuals.json",
  easyProjectsPath: "/public/easy-doc/Projects.json",
});
```



-   Easydoc.init 函数参数说明

| 参数               | 类型                         | 必填 | 默认值                       | 说明                                          |
| ---------------- | -------------------------- | -- | ------------------------- | ------------------------------------------- |
| easyDocPath      | string                     | 否  | '/easy-doc/EasyDoc.json'  |                                             |
| easyManualsPath  | string                     | 否  | '/easy-doc/Manuals.json'  |                                             |
| easyProjectsPath | string                     | 否  | '/easy-doc/Projects.json' |                                             |
| minHeight        | number                     | 否  | 100                       | 文档节点弹窗最小高度                                  |
| minWidth         | number                     | 否  | 200                       | 文档节点弹窗最小宽度                                  |
| maxWidth         | number                     | 否  | 450                       | 文档节点弹窗最大宽度                                  |
| editHeight       | number                     | 否  |                           | 可编辑节点弹窗固定高度                                 |
| editWidth        | number                     | 否  |                           | 可编辑节点弹窗固定宽度                                 |
| urlPrefix        | string                     | 否  |                           | 静态资源路径前缀，自动添加到所以easydoc请求前面                 |
| env              | (() => AuthEnum) \| string | 否  | 'DEVELOPMENT'             | 当前文档可见范围'DEVELOPMENT'> 'TEST' >'PRODUCTION' |
| showGuideMask    | boolean                    | 否  | false                     | 节点展示时，下方是否显示半透明蒙层                           |
| mountPanel       | boolean                    | 否  | true                      | 是否挂载右上角面板                                   |
| ignorePaths      | string[]                  | 否  | []                       | 不启用easydoc的页面路径数组                           |
| hasEasyDocJSON   | boolean                    | 否  | true                      | 是否请求Easydoc.json文件                          |
| hasManualsJSON   | boolean                    | 否  | true                      | 是否请求Manuals.json文件                          |
| hasProjectsJSON  | boolean                    | 否  | true                      | 是否请求Projects.json文件                         |


-   env 参数扩展讲解
    -   'dev' 或 'DEVELOPMENT' 表示生产环境、测试环境、开发环境可见所有文档
    -   'test' 或 'TEST' 表示生产环境、测试环境可见所有文档
    -   'pro' 或 'PRODUCTION' 表示生产环境可见所有文档

```javascript
// 可以指定权限 dev > test > pro
EasyDoc.init({
  env: 'pro', // dev | test | pro
})
// 可以传入函数计算求值
EasyDoc.init({
  env: () => {
    switch (process.env.NODE_ENV) {
      case 'production':
        return 'pro'
      case 'test':
        return 'test'
      case 'development':
        return 'dev'
      default:
        return 'pro'
    }
  },
})
// 可以根据域名后缀判断
EasyDoc.init({
  env: () => {
    if (window.location.href.indexOf('.guahao.cn') > -1) {
      return 'pro'
    }
    if (window.location.href.indexOf('.guahao-test.com') > -1) {
      return 'test'
    }
    return 'dev'
  },
})
```
### 3. 编写项目文档

项目文档是对整个项目的介绍说明、注意事项备注等，在项目第一次打开时自动弹出，此后不再自动弹出，清除浏览器缓存失效；也可通过点击右上角项目文档查看。

-   public/easy-doc/Projects.json（静态文件夹也可能是static而不是public）
-   name：项目文档名称
-   description：项目文档内容
-   可编写纯文字或插入html ，特别是跳转a链接
-   auth：项目文档可见范围
-   可以编写多个项目文档，如无项目文档，跳过此步

```json
[
  {
    "name": "Diting最佳实践",
    "description": "Diting最佳实践的详细介绍Diting最佳实践的详细介绍Diting最佳实践的详细介绍Diting最佳实践的详细介绍Diting最佳实践的详细介绍",
    "auth": "pro"
  },
  {
    "name": "Gtrace-最佳实践",
    "description": "Gtrace-最佳实践的详细介绍Gtrace-最佳实践的详细介绍Gtrace-最佳实践的详细介绍Gtrace-最佳实践的详细介绍Gtrace-最佳实践的详细介绍",
    "auth": "pro"
  },
  {
    "name": "Kano最佳实践",
    "description": "Kano最佳实践的详细介绍Kano最佳实践的详细介绍Kano最佳实践的详细介绍Kano最佳实践的详细介绍Kano最佳实践的详细介绍Kano最佳实践的详细介绍",
    "auth": "pro"
  },
  {
    "name": "MQ最佳实践",
    "description": "MQ最佳实践的详细介绍MQ最佳实践的详细介绍MQ最佳实践的详细介绍MQ最佳实践的详细介绍MQ最佳实践的详细介绍MQ最佳实践的详细介绍",
    "auth": "pro"
  },
  {
    "name": "配置中心gconfig 最佳实践",
    "description": "配置中心gconfig 最佳实践的详细介绍配置中心gconfig 最佳实践的详细介绍配置中心gconfig 最佳实践的详细介绍配置中心gconfig 最佳实践的详细介绍配置中心gconfig 最佳实践的详细介绍",
    "auth": "pro"
  }
]
```

### 4. 编写页面文档

页面文档是对某个页面的介绍说明，注意事项的备注。通过Easydoc.json指定页面和json文件的映射关系，再在json文件中编写。

-   public/easy-doc/Easydoc.json
-   match：匹配路由的正则表达式
-   jsonFile：对应的json文件路径

```json
[
  {
    "match": "/user/list",
    "jsonFile": "/public/easy-doc/user3.json"
  },
  {
    "match": "/dept/list/[0-9]+",
    "jsonFile": "/public/easy-doc/dept.json"
  },
  {
    "match": "/handle-doc.html",
    "jsonFile": "/public/easy-doc/handle-doc.json"
  },
]
```

-   public/easy-doc/user3.json
-   name：页面说明名称
-   description：页面说明内容
-   auth：页面说明可见范围

```json
{
  "pages": [
    {
      "name": "第一个user页面介绍",
      "description": "这是一段内容",
      "auth": "dev"
    },
    {
      "name": "第一个user页面介绍",
      "description": "这是又一段内容",
      "auth": "test"
    }
  ],
}
```

### 5. 编写页面节点文档

页面节点文档是对某个页面的某个节点的介绍说明，注意事项的备注。通过Easydoc.json指定页面和json文件的映射关系，再在json文件中编写文档，在页面的dom节点上添加docId实现映射。

-   public/easy-doc/Easydoc.json
-   match：匹配路由的正则表达式
-   jsonFile：对应的json文件路径

```json
[
  {
    "match": "/user/list",
    "jsonFile": "/public/easy-doc/user3.json"
  },
  {
    "match": "/dept/list/[0-9]+",
    "jsonFile": "/public/easy-doc/dept.json"
  },
  {
    "match": "/handle-doc.html",
    "jsonFile": "/public/easy-doc/handle-doc.json"
  },
]
```

-   public/easy-doc/user3.json
-   name：页面说明名称
-   description：页面说明内容
-   auth：页面说明可见范围
-   direction：节点弹窗方位，非必填
-   zIndex：指定zIndex防止遮挡，非必填

```json
{
  "docs": [
    {
      "docId": "dept-list",
      "description": "当切换为运行状态时当切换为运行状态时当切换为运行状态时",
      "auth": "pro",
      "direction": "LT",
      "zIndex": 100
    },
    {
      "docId": "dept-btn",
      "description": "方方速递速速递速速递速递对，个按按钮方速递对，一个按按钮方速递对，",
      "auth": "dev",
      "direction": "BR"
    }
  ],
}
```

-   /user/list对应的vue文件

```html
<div>
  <div docId='dept-list'>
    user list 页面 html
  <div>
    <el-button docId='dept-btn'>
    user list 页面 的 btn
  <div>
</div>
```

### 6. 编写可编辑节点文档

可编辑节点文档用于前台系统展示，后面系统编辑前台展示内容的场景。在此场景中将前台某块内容和后台对该内容的编辑页面连接起来，点击直接跳转过去进行配置，方便产品运营的使用。通过Easydoc.json指定页面和json文件的映射关系，再在json文件中编写文档，在页面的dom节点上添加docId实现映射。

-   public/easy-doc/Easydoc.json
-   match：匹配路由的正则表达式
-   jsonFile：对应的json文件路径

```json
[
  {
    "match": "/user/list",
    "jsonFile": "/public/easy-doc/user3.json"
  },
  {
    "match": "/dept/list/[0-9]+",
    "jsonFile": "/public/easy-doc/dept.json"
  },
  {
    "match": "/handle-doc.html",
    "jsonFile": "/public/easy-doc/handle-doc.json"
  },
]
```

-   public/easy-doc/user3.json
-   name：页面说明名称
-   description：页面说明内容
-   auth：页面说明可见范围
-   direction：节点弹窗方位，非必填
-   zIndex：指定zIndex防止遮挡，非必填

```json
{
  "edits": [
    {
      "docId": "dept-list",
      "editUrl": "https://fanyi.baidu.com/translate?aldtype=16047&keyfrom=baidu&smartresult=dict&lang=auto2zh#ru/zh/EasyDoc",
      "auth": "dev",
      "direction": "TL",
      "zIndex": 200
    },
    {
      "docId": "dept-btn",
      "editUrl": "https://fanyi.baidu.com/translate?aldtype=16047&keyfrom=baidu&smartresult=dict&lang=auto2zh#ru/zh/EasyDoc",
      "auth": "test",
      "direction": "LB"
    }
  ],
}
```

-   /user/list对应的vue文件

```html
<div>
  <div docId='dept-list'>
    user list 页面 html
  <div>
    <el-button docId='dept-btn'>
    user list 页面 的 btn
  <div>
</div>
```

### 7. 编写操作手册

操作手册是动态实时可操作的使用说明书，点击可以自动跳到操作手册对应的第一个页面，跟着步骤一步一步的实践动手，方便新手更好的学习系统的使用、了解功能背后隐藏的业务信息。

-   public/easy-doc/Manuals.json
-   注意：通过指定type=link，linkManualName=操作手册名称，可以实现从一个操作手册跳到另一个操作手册
-   可以在步骤的description中添加a链接，实现外链跳转
-   记得要在对应页面的dom中加上步骤中的docId哦

```json
[
   {
    "name": "操作手册A",
    "description": "这是关于操作手册A的描述<a href='http://wcp.gops.guahao.cn/frontend-refactor/home/page'>去WCP</a>",
    "initUrl": "/dept/list", // 打开操作手册的时候会跳到此初始url
    "steps": [
      {
        "url": "/dept/list",
        "description": "操作手册A第一步有两个按钮高亮",
        "nodes": [
          {
            "docId": "dept-open-btn1",
            "description": "操作手册A第一步节点1",
            "auth": "pro",
            "zIndex": 1000 // 指定zIndex防止遮挡，非必填
          },
          {
            "docId": "dept-open-btn2",
            "description": "操作手册A第一步节点2",
            "auth": "pro"
          }
        ]
      },
      ..steps // 多个步骤此处省略
      
  {
    "name": "操作手册B",
    "description": "这是关于操作手册B的描述",
    "initUrl": "/user/list", // 打开操作手册的时候会跳到此初始url
    "steps": [
      {
        "url": "/user/list",
        "description": "操作手册B第一步有两个按钮高亮",
        "nodes": [
          {
            "docId": "dept-open-btn2",
            "description": "操作手册A第一步节点2",
            "auth": "pro"
          }
        ]
      },
       {
        "description": "点击从操作手册B直接跳到操作手册A",
        "type": "link",
        "linkManualName": "操作手册A"
      }
    ]
]
```

### 8. 编写用户引导

用户引导是固定的步骤引导，一般用于新功能的第一次使用时介绍如何使用。

-   EasyDoc.initGuide(guide: GuideNode) 初始化用户引导数据
-   EasyDoc.startGuide() 开始当前的用户引导
-   EasyDoc.jumpGuideStep(stepIdx: number, guideStep?: GuideStep) 跳到当前用户引导的第几步，从0计数；第二个参数传入表示替换当前步骤内容
-   EasyDoc.closeGuide() 主动关闭当前操作手册

```javascript
  // 初始化用户引导数据
  EasyDoc.initGuide({
    'name': '用户引导A',
    'steps': [
      {
        'url': '/dept/list',
        'node': {
          'docId': 'guide1',
          'description': '用户引导<br />A第一步节点1',
          'auth': 'pro'
        }
      },
      {
        'url': '/dept/list',
        'node': {
          'docId': 'guide2',
          'description': '用户引导A第一步节点2',
          'auth': 'pro'
        }
      },
      {
        'url': '/dept/list',
        'node': {
          'docId': 'guide3',
          'description': '用户引导A第一步节点3',
          'auth': 'pro'
        }
      },
      {
        'url': '/dept/list',
        'node': {
          'docId': 'guide4',
          'description': '用户引导A第一步节点4',
          'auth': 'pro'
        }
      },
      {
        'url': '/dept/list',
        'node': {
          'docId': 'guide5',
          'description': '用户引导A第一步节点5',
          'auth': 'pro'
        }
      },
      {
        'url': '/dept/list',
        'node': {
          'docId': 'guide6',
          'description': '用户引导A第一步节点6',
          'auth': 'pro'
        }
      },
    ]
  })
  // 开始当前用户引导
  EasyDoc.startGuide()
  // 4秒后跳到用户引导第4步，并修改第4步内容，并不显示下一步按钮
  setTimeout(() => {
    EasyDoc.jumpGuideStep(3, {
      'url': '/dept/list',
      'node': {
        'docId': 'guide4',
        'description': '手动修改内容',
        'auth': 'pro'
      },
      next: false,//是否显示下一步按钮
    },)
  }, 4000)
  // 再3秒后关闭当前用户引导
  setTimeout(() => {
    EasyDoc.closeGuide()
  }, 7000)
```

## EasyDoc扩展用法

### 1. docId的多种兼容写法

-   docId、doc-id、docid、data-docId、data-doc-id、data-docid都可以匹配
-   docId不能以数字开头
-   一个dom节点上可以写多个docId，用空格隔开
-   单个docId也可以匹配当前页面的多个dom节点，设置noUnique=true即可，默认一个页面只匹配一个dom节点

```html
<div docId="user-list-query user-list-search"></div>
<div docId="user-btn user-list-query"></div>

{
  "docs": [
    {
      "docId": "user-btn-query",
      "description": "点击查询用户列表",
      "auth": "dev",
      "direction": "BL",
      "noUnique": true //单个docId也可以匹配当前页面的多个dom节点
    }
  ]
}
```

### 2. direction弹窗方位的说明

-   direction是可选属性，默认自适应位置，用户可以指定方位来调整显示效果
-   TL 上左
-   TR 上右
-   TC 上中
-   RT 右上
-   RB 右下
-   RC 右中
-   BL 下左
-   BR 下右
-   BC 下中
-   LT 左上
-   LB 左下
-   LC 左中

### 3. 路径前缀
- 某些系统会配置url前缀，比如某网站http://www.baidu.com 对应的json文件地址为：http://www.baidu.com/easy-doc/Easydoc.json, 当其配置了前缀 frontend-refactor 使得访问路径变成了http://www.baidu.com/frontend-refactor, 导致json文件找不到了。我们只需要在初始化时增加urlPrefix参数即可。

```javascript
  EasyDoc.init({
    urlPrefix: "/frontend-refactor",
    easyDocPath: "/public/easy-doc/EasyDoc.json",
    easyManualsPath: "/public/easy-doc/Manuals.json",
    easyProjectsPath: "/public/easy-doc/Projects.json",
  });
```

-   假设某网站线上地址和测试地址不一致那应该怎么办呢？方案如下：

```javascript
let urlPrefix = ``
let easyDocPath = `/public/easy-doc/EasyDoc.json`
let easyManualsPath = `/public/easy-doc/Manuals.json`
let easyProjectsPath = `/public/easy-doc/Projects.json`
// 线上
if (location.origin === 'http://xxxxx') {
  urlPrefix = `/frontend-refactor`
  easyDocPath = `http://xxxxx/frontend-refactor/public/easy-doc/EasyDoc.json`
  easyManualsPath = `http://xxxxx/frontend-refactor/public/easy-doc/Manuals.json`
  easyProjectsPath = `http://xxxxx/frontend-refactor/public/easy-doc/Projects.json`
}
EasyDoc.init({
  urlPrefix,
  easyDocPath,
  easyManualsPath,
  easyProjectsPath
})
```

### 4. 清除F12 network 找不到json文件报错404

-   我们默认会请求public/easy-doc/EasyDoc.json、Manuals.json、Projects.json文件，但是该项目可能暂时并没有配置该文档，所以network里面就会报404找不到该文件。
-   这个问题并不影响业务，但是业务方找业务bug的时候看到Easydoc的404错误总是怀疑Easydoc有问题，所以特此优化处理一下。

```javascript
EasyDoc.init({
  hasEasyDocJSON: false, //默认true, 设为false则不请求该json
  hasManualsJSON: false, //默认true, 设为false则不请求该json
  hasProjectsJSON: false, //默认true, 设为false则不请求该json
});
```

### 5. CHANGLOG.md

通过此文件可以看到每次更新的内容介绍和对应的版本，了解EasyDoc的历史发展


## 向前走、别回头

当然目前开源的只是EasyDoc的冰山一角，我们的规划的未来全貌是：
- EasyDoc主包：加载面板和弹窗，`动态加载其他SDK副包`
- EasyDoc可视化配置副包：提供可视化新增编写json业务文档的能力
- EasyDoc源码和页面元素映射副包：提供点击页面div找到对应vue标签位置的能力
- EasyDoc用户行为分析反馈收集副包：提供收集用户行为和反馈意见的能力
- EasyDoc文档管理后台：`提供存放和修改业务文档的能力，实现文档和项目完全解耦，最终建设成为集团文档的收录系统`


通往成功的路从来都不是一帆风顺的，路上曲折坎坷却令人着迷。在EasyDoc架构自研的道路上，我们经历过一腔热血加油干的激情，也经历过自我怀疑没意义的低谷，既经历过老板用户的表扬创意非常好的鼓励，也经历过用户无情的吐槽真特么难用。`我们能做的只有坚持不懈、化茧成蝶😎😎`。当我们走完这段路程回头来看，还是很感谢这段经历带给我们的成长的。`虽然我们的产品可能无法带给社区多大的帮助多大的声音，但是我们也希望以我们的经历带给大家一些启发和信心💖💖`，启发同学们做成更优先的架构自研产品，给正在架构自研路上的同学们一点信心你们一定会成功的。`向前走、别回头，路上春色正好，天上太阳正晴✌✌`。

## 开发维护人员
- [李运通](https://juejin.cn/user/1292681403180136) 😜😜
- [杨毅臻](https://juejin.cn/user/1679709496940616) 😎😎
- [胡宁](https://juejin.cn/user/2928754708718168) ✌✌
- [焦传锴](https://juejin.cn/user/1266247427691405) 😉😉
- [权明扬](https://juejin.cn/user/4125023356589831) 😘😘
- [黄丹丹](https://juejin.cn/user/3729960318014471)🤞🤞


## EasyDoc gitbub地址
https://github.com/wefront/we-easydoc

记得给我们`点赞`✨✨点个star哟🤞🤞（づ￣3￣）づ╭❤～






