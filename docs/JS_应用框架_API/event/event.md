# 控件 Event

## Button 控件

- `event` 事件对象示例

    `{type : "tap",timeStamp : 3314.000000,target : {id : "button"},currentTarget : {id : "button"}}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |

## Checkbox 控件

- `event` 事件对象示例

    `{type : "change",timeStamp : 855134.000000,target : {id : "checkbox"},currentTarget : {id : "checkbox"},detail : {value : true}}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | detail | Object | 额外的信息 | 有 `{value : true}` 或 `{value : false}` 分别对应控件状态选中或未选中|

## Switch 控件

- `event` 事件对象示例

    `{type : "change",timeStamp : 696273.000000,target : {id : "switch"},currentTarget : {id : "switch"},detail : {value : true}}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | detail | Object | 额外的信息 | 有 `{value : true}` 或 `{value : false}` 分别对应控件状态开或关|

## Card 控件

- `event` 事件对象示例

    `{type : "change",timeStamp : 3314.000000,target : {id : "card"},currentTarget : {id : "card"},detail : {value : 0}}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 | 事件类型 ¹ 有 `dropBegin、dropFirst、dropLast、dropStart、change、unchange、dropEnd` |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | detail | Object | 额外的信息 | `{value : 0}` 对应当前页号|

    > ¹ dropBegin：在第一页往前切时触发且只在第一页触发、<br/>
    dragFirst：在 card 第一项向前一项滑动后触发、<br/>
    dragStart：在 card 按下后触发、<br/>
    change：在 card 切换前后项成功后触发、<br/>
    unchange：在 card 未切换前后项触发、<br/>
    dropEnd：在最后一页往前切时触发且只在最后一页触发、<br/>
    dragLast：在 card 最后一项向后一项滑动后触发`

## ListCtrl 控件

- `event` 事件对象示例

    `{type : "change", timeStamp : 1000.000000, target : {id : "listctrl1"}, currentTarget : {id : "listctrl1"}, detail : {value : true}}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 | 事件类型 ¹ 有  `dropFirst、start、change、dropLast` |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | detail | Object | 额外的信息 | `{value : true}` 表示在第一条目上向前拉到底，`{value: false}` 表示在最后条目向后拉到底 |
    > ¹ dropFirst：拉过第一项时，松手后触发、<br/>
    start：开始滑动时触发、<br/>
    change：滑动结束时触发、<br/>
    dropLast：滑到最后一项触发

## Slider 控件

- `event` 事件对象示例

    `{type : "change",timeStamp : 3314.000000,target : {id : "slider"},currentTarget : {id : "slider"},detail : {value : 50}}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | detail | Object | 额外的信息 | `{value : 50}` 对应当前值|

## WheelImage 控件

- `event` 事件对象示例

    `{type : "change",timeStamp : 3314.000000,target : {id : "wheelImage"},currentTarget : {id : "wheelImage"},detail : {value : 1}}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | detail | Object | 额外的信息 | `{value : 1}` 对应当前选中项|

## WheelString 控件

- `event` 事件对象示例

    `{type : "change",timeStamp : 3314.000000,target : {id : "wheelString"},currentTarget : {id : "wheelString"},detail : {value : 1}}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | detail | Object | 额外的信息 | `{value : 1}` 对应当前选中项|


## Panel 控件

- `event` 事件对象示例

    `{type : "touch",timeStamp : 2292.000000,target : {id : "Panel1"},currentTarget : {id : "Panel1"},touchs : [{identifier : 2240.000000,x : 80.000000,y : 59.000000,type : "touchstart"}, ]}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | touchs | Array | 触摸事件，触摸点信息的数组 | `identifier` 触点ID; `x,y` 坐标值; `type` 事件类型 ¹ 有 `touchstart touchmove touchlong touchend`|

    > ¹ touchstart：触摸开始时触发、<br/>
     touchmove：触摸短距离移动时触发、<br/>
     touchlong：长时间点击或短距离移动时触发、<br/>
     touchend：触摸结束时触发、

## Page 控件

- `event` 事件对象示例

    `{type : "touch",timeStamp : 2292.000000,target : {id : "Page1"},currentTarget : {id : "Page1"},touchs : [{identifier : 2240.000000,x : 80.000000,y : 59.000000,type : "touchstart"}, ]}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | touchs | Array | 触摸事件，触摸点信息的数组 | `identifier` 触点ID; `x,y` 坐标值; `type` 事件类型 ¹ 有 `touchstart touchmove touchlong touchend`|

    > ¹ 同 panel 控件


## textbox 控件

- `event` 事件对象示例

    `{type : "change", timeStamp : 23168.000000, target : {id : "textbox1"}, currentTarget : {id : "textbox1"}, detail : {value : "q"}}`

- `event` 属性

    | 属性名  | 类型 | 描述 | 注解 |
    | - | - | - | - |
    | type | String | 事件类型 |
    | timeStamp | Number | 事件触发时间戳 |
    | target | Object | 触发事件的控件的一些属性值集合 |
    | currentTarget | Object | 当前组件的一些属性值集合 |
    | detail | Object | 额外的信息 | `{value : "q"}` 对应变化后的新值|

## Demo

- 以 listctrl 的 event 事件为例

- 当滑倒底部时给予用户提示：`没有更多项...`

  1. 在设计页面拖入一个 listctrl 控件
  2. 依次往 listctrl 内拖入六个 label
  3. 选中 listctrl 控件在 *属性栏 --> 调用属性* 输入 `ShowEvent` 然后敲回车，再双击该输入框左侧进入代码页面，复制以下 ShowEvent 函数到代码
  4. 点击运行按钮，往上拖动 listctrl 内的控件，当滑倒底部时，最后一个控件显示文本由 `label6` 到 `没有更多项...` 。

 ```js
 ShowEvent: function (event) {
    console.dir(event);
    // 判断 event 类型是否为划到最底部
    if (event.type == "dropLast") {
        this.setData({label6:'没有更多项...'})
    }
}
 ```