# JS SDK

ReleaseNote

| 版本  | 时间              | 修改内容 |
| ----- | ----------------- | -------- |
| 1.0.0 | 2022 年 3 月 3 号 | init     |

### 步骤一：引入资源

```html
<meta name="spm-id" content="10155" />
<link
  rel="stylesheet"
  href="https://static.1lan.tv/Transformers/Brawn/ylplayer/prod/1.0.9/ylplayer.min.css"
/>
<script
  type="text/javascript"
  src="https://static.1lan.tv/Transformers/Starscream/ylspm/0.0.1/index.js"
></script>
<script
  type="text/javascript"
  src="https://static.1lan.tv/Transformers/Starscream/vaassdk/0.0.1/index.js"
></script>
<script
  type="text/javascript"
  src="https://static.1lan.tv/Transformers/Brawn/ylplayer/prod/1.0.9/ylplayer.min.js"
></script>
```

### 步骤二：初始化

JSSDK 提供了 初始化方法，用于初始化 JSSDK，注入的参数将自动应用到 JSSDK 内部所有模块，全局只调用一次即可。

```js
var VaaS = new VaaSSDK({
  access_key: 'your access_key', //应用的access_key
  access_token: 'your access_token', //应用的access_token
  debug: true, //是否开启打印
})
```

### 步骤三：开始使用

#### 获取视频信息流

接口请求参数和返回参数详见 VaaS API：[获取视频信息流](../api/feed-flow.md)

```js
VaaS.getFeed(
  {
    channel_id: 1291,
    video_type: 1,
    load_type: 2,
    size: 8,
  },
  function (res) {
    console.log('getFeed', res)
  }
)
```

#### 获取推荐信息流列表

接口请求参数和返回参数详见 VaaS API：[获取推荐信息流列表](../api/feed-flow.md)

```js
VaaS.getRelation(
  {
    id: '视频id',
    size: 8,
  },
  function (res) {
    console.log('getRelation', res)
  }
)
```

#### 获取视频频道

接口请求参数和返回参数详见 VaaS API：[获取推荐相关](../api/feed-flow.md)

```js
VaaS.getChannels(
  {
    video_type: 1,
  },
  function (res) {
    console.log('getChannels', res)
  }
)
```

#### 获取视频详情

接口请求参数和返回参数详见 VaaS API：[获取视频详情](../api/feed-flow.md)

```js
VaaS.getVideos(
  {
    ids: '视频id1,视频id2',
    video_type: 1,
  },
  function (res) {
    console.log('getVideos', res)
  }
)
```

#### 获取视频播放信息

接口请求参数和返回参数详见 VaaS API：[获取视频播放信息](../api/feed-flow.md)

```js
VaaS.getPlay(
  {
    id: '视频id',
  },
  function (res) {
    console.log('getPlay', res)
  }
)
```

#### 获取作者详情

接口请求参数和返回参数详见 VaaS API：[获取作者详情](../api/feed-flow.md)

```js
VaaS.getCpInfo(
  {
    id: '作者id',
    video_type: 1,
  },
  function (res) {
    console.log('getCpInfo', res)
  }
)
```

#### 获取作者视频列表

接口请求参数和返回参数详见 VaaS API：[获取作者视频列表](../api/feed-flow.md)

```js
VaaS.getCpVideos(
  {
    video_type: 1,
    id: '作者id',
    page: 1,
    size: 8,
  },
  function (res) {
    console.log('getRelation', res)
  }
)
```

#### 播放器

```js
// 完整调用方式
let player = null
function getPlayer() {
  player = new YLPlayer({
    container: document.getElementById('J_ylplayer'), // 承载H5播放器容器元素ID
    trackLogParams: {
      videoId: '视频id', // 视频ID
      accesskey: 'your access_key', // 渠道key
    },
  })
}

/**
   如果点击视频时异步切换视频调用方式如下：
**/
// 第一步先销毁当前播放器然后重新创建
player.destroy()
// 第二步重新创建播放器实例
getPlayer()
```

