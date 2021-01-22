## Navigate

### pm.navigateTo(url `or` obj)

保留当前页面，跳转到新页面，使用 `pm.navigateBack()` 可以返回到原页面。

| 参数 | 类型   | 描述 | 示例  |
|------|--------|----------------------------------------|--------------------------|
| url  | String | 需要跳转的新页面路径 | `pm.navigateTo('page/main')` |
| obj  | Object | 包含需要跳转的新页面路径，以及相关参数¹ | `pm.navigateTo({url : 'page/main'})` , `pm.navigateTo({url : 'page/main', value : 123})` |

> ¹ 该参数在新页面的 onLoad 函数内接收，url 与 value 是关键字，不能修改为其他。

`* url 为基于工程目录的相对路径，value 为传到目标页的信息。page/main：代表 page 文件夹的下的名称为 main 的页面文件，page 的保存路径为当前 page 名称的文件夹下的 page 名称对应的文件，即 pageName/pageName `

### pm.redirectTo(url `or` obj)

关闭当前页面，跳转到新页面。

| 参数 | 类型   | 描述 | 示例  |
|------|--------|----------------------------------------|--------------------------|
| url  | String | 需要跳转的新页面路径                   | `pm.redirectTo('page/main')` |
| obj  | Object | 包含需要跳转的新页面路径，以及相关参数¹ | `pm.redirectTo({url : 'page/main'})`,`pm.redirectTo({url : 'page/main', value : 123})` |

### pm.navigateBack()

返回到当前一级或多级上一级的 Page，并关闭当前一级或者多级 Page。

 - pm.navigateBack()

    无参数，用于返回上级 Page，并关闭当前 Page。

- pm.navigateBack(value)
    
  用于返回上级 Page，并关闭当前 Page，同时将 value 返回给上级 Page，作为上级 Page 的 onUpdate 函数的入参，上级 Page 需要有 onUpdate(event) 函数存在。

- pm.navigateBack(value，number)

    用于返回多级 Page，并关闭当前 Page。`注：value必填，但只有返回到的 Page 有 onUpdate 函数的时候才有使用意义，其他情况下一般填 null; number 代表要返回的 Page 级数。`

### pm.closePage(pageName)

关闭指定 Page 页面，参数 `name` 为要关闭的 Page 页面的名称。
```js
// 关闭 page1 页面
pm.closePage('page1')
```

### pm.getPages()

 获取当前的页面栈，返回值 Number 类型，用于获取当前存在的 Page 个数。详见下文示例代码。

### pm.getPageName()

 获取当前页面的名称，返回值 String 类型，如 `"page1"`。详见下文示例代码。

### pm.getPagesName()

 获取当前所有已打开页面的名称，返回值 Array 类型，如 `["page2", "page1"]`。详见下文示例代码。

### pm.getPageObject()

 获取当前 Page 页面对象，返回值 Object 类型，包含用户自定义的函数、变量等。详见下文示例代码。

## 示例

例如从 page1 使用 pm.navigateTo(url `or` obj) 函数依次跳转到 page4 : page1 --> page2 --> page3 --> page4。
        
- 在 page4 代码页面使用 pm.navigateBack() 表示返回到 page3。
- 在 page4 代码页面使用 pm.redirectTo('page3/page3') 表示关闭当前页跳转到 page3，此时 page4 已被释放。
- 在 page4 代码页面使用 pm.navigateBack(null, 3) 表示往前返回三级页面，即返回到 page1 页面。此时 page2、page3、page4 的内存会被释放掉。
- 在 page4 代码页面使用 pm.getPages() 命令窗输出结果：`4` ，表示已打开的页面数量有4个。
- 在 page4 代码页面使用 pm.getPageName() 命令窗输出结果：`"page4"` ，表示当前页面的Name值。
- 在 page4 代码页面使用 pm.getPagesName() 命令窗输出结果：`["page4", "page3", "page2", "page1", ]`，表示当前已打开的所有页面。
- 在 page4 代码页面使用
   - pm.closePage('page3') 表示关闭 page 名为 page3 的页面，此时再使用 pm.getPagesName() 只会输出 `["page4", "page2", "page1", ]`。
   - pm.closePage('page4') 则会返回到 page3，因为 page4 已经关闭。
- 在 page4 代码页面使用 pm.getPageObject() 命令窗输出结果：`{onLoad : [function], onResume : [function], onShow : [function], onHide : [function], onExit : [function], click : [function], inputStr : "", txtchange : [function], setData : [function], getData : [function], getMouseOwner : [function], requestAnimationFrame : [function], addListener : [function], removeListener : [function]}`，表示当前页面所有信息，其中 `click, inputStr, txtchange` 是页面的函数以及变量。