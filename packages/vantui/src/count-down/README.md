# CountDown 倒计时

### 介绍

用于实时展示倒计时数值，支持毫秒精度。

### 引入

在 Taro 文件中引入组件

```js
import { CountDown } from '@antmjs/vantui'
```

> Vant Weapp 1.0 版本开始支持此组件，升级方式参见[快速上手](#/quickstart)。

## 代码演示

### 基本用法

`time`属性表示倒计时总时长，单位为毫秒。

::: $demo1 :::

### 自定义格式

通过`format`属性设置倒计时文本的内容。

::: $demo2 :::

### 毫秒级渲染

倒计时默认每秒渲染一次，设置`millisecond`属性可以开启毫秒级渲染。

::: $demo3 :::

### 自定义样式

通过`onChange`事件获取`timeData`对象并自行渲染，格式见下方表格。

::: $demo4 :::

### 手动控制

通过 `ref` 选择器获取到组件实例后，可以调用`start`、`pause`、`reset`方法。

::: $demo5 :::

### ICountDownRef [[详情]](https://github.com/AntmJS/vantui/tree/main/packages/vantui/types/count-down.d.ts)

| 参数  | 说明                                                     | 类型                                    |
| ----- | -------------------------------------------------------- | --------------------------------------- |
| start | 开始倒计时                                               | _&nbsp;&nbsp;()&nbsp;=>&nbsp;void<br/>_ |
| pause | 暂停倒计时                                               | _&nbsp;&nbsp;()&nbsp;=>&nbsp;void<br/>_ |
| reset | 重设倒计时，若 autoStart 为 true，重设后会自动开始倒计时 | _&nbsp;&nbsp;()&nbsp;=>&nbsp;void<br/>_ |

### ITimeData [[详情]](https://github.com/AntmJS/vantui/tree/main/packages/vantui/types/count-down.d.ts)

| 参数         | 说明     | 类型                      |
| ------------ | -------- | ------------------------- |
| days         | 剩余天数 | _&nbsp;&nbsp;number<br/>_ |
| hours        | 剩余小时 | _&nbsp;&nbsp;number<br/>_ |
| minutes      | 剩余分钟 | _&nbsp;&nbsp;number<br/>_ |
| seconds      | 剩余秒数 | _&nbsp;&nbsp;number<br/>_ |
| milliseconds | 剩余毫秒 | _&nbsp;&nbsp;number<br/>_ |

### CountDownProps [[详情]](https://github.com/AntmJS/vantui/tree/main/packages/vantui/types/count-down.d.ts)

| 参数        | 说明                                           | 类型                                                                                                                                                                     | 默认值     | 必填    |
| ----------- | ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | ------- |
| millisecond | 是否开启毫秒级渲染                             | _&nbsp;&nbsp;boolean<br/>_                                                                                                                                               | false      | `false` |
| time        | 倒计时时长，单位毫秒                           | _&nbsp;&nbsp;number<br/>_                                                                                                                                                | -          | `false` |
| format      | 时间格式，DD-日，HH-时，mm-分，ss-秒，SSS-毫秒 | _&nbsp;&nbsp;string<br/>_                                                                                                                                                | HH：mm：ss | `false` |
| autoStart   | 是否自动开始倒计时                             | _&nbsp;&nbsp;boolean<br/>_                                                                                                                                               | true       | `false` |
| children    | 倒计时的内容                                   | _&nbsp;&nbsp;ReactNode<br/>_                                                                                                                                             | -          | `false` |
| onChange    | -                                              | _&nbsp;&nbsp;(timeData:&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;detail:&nbsp;ITimeData<br/>&nbsp;&nbsp;})&nbsp;=>&nbsp;void<br/>_                                             | -          | `false` |
| onFinish    | 倒计时结束时触发                               | _&nbsp;&nbsp;()&nbsp;=>&nbsp;void<br/>_                                                                                                                                  | -          | `false` |
| ref         | 倒计时实例                                     | _&nbsp;&nbsp;React.MutableRefObject<<br/>&nbsp;&nbsp;&nbsp;&nbsp;&brvbar;&nbsp;ICountDownRef<br/>&nbsp;&nbsp;&nbsp;&nbsp;&brvbar;&nbsp;undefined<br/>&nbsp;&nbsp;><br/>_ | -          | `false` |

### 样式变量

组件提供了下列 CSS 变量，可用于自定义样式，使用方法请参考[ConfigProvider 组件](https://antmjs.github.io/vantui/#/config-provider)

| 名称                     | 默认值            |
| ------------------------ | ----------------- |
| --count-down-text-color  | ` @text-color;`   |
| --count-down-font-size   | ` @font-size-md;` |
| --count-down-line-height | ` 40px;`          |
