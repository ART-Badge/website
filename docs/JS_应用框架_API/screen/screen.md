# 背光

## pm.setScreenBrightness(value)

设置背光。

| 参数 | 类型 | 描述 | 示例 |
| - | - | - | - |
| value | Number | 背光亮度 0 ~ 100，默认 100。 | `pm.setScreenBrightness({value : 800})` |

`* 设值大于 100 将设置为 100，小于 0 不做处理。`

## pm.getScreenBrightness()

获取当前背光亮度。

```js
console.dir(pm.getScreenBrightness());  // 获取到当前设值得背光亮度值。
```