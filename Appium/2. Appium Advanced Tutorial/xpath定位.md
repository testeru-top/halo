## 包含-contains()
-  `Xpath` 表达式中的一个函数
-  `contains()`函数匹配==属性值==中包含的==字符串==
#### contains+text
- `appium` 中 `text` 属性对应的文本就是显示的内容
```
//*[contains(@text,"阿里")]
```
![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121545975.png)


#### contains+属性
```
//*[contains(@resource-id,"stock")]
```

![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121547772.png)

### 总结
- `contains()` 函数定位的元素很容易为 `list`
- `contains()` 函数内的属性名需要用 `@`开始
# XPath轴
## 父子-parent

#### 当前节点的父节点 
```
//*[@text="HK"]/..

//*[@text="HK"]/parent::*
```
![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121645090.png)
![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121645090.png)


#### 当前节点的子节点
## 爷孙-parent
#### 当前节点的爷爷
- 当前节点的父级的父级
```
//*[@text="HK"]/../..

//*[@text="HK"]/parent::*/parent::*
```
![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121647574.png)
#### 当前节点的孙子
## 祖先-ancestor
 - `ancestor` 用于在指定层查找特定成员的祖先的函数。
 - 可以显式指定要返回的祖先级别或祖先相对于成员级别的级别。它从祖先返回分层步骤数，定位用户想要的指定祖先。
 - 返回当前节点的所有祖先
#### 返回当前节点的所有祖先

```
//*[@text="HK"]/ancestor::android.widget.RelativeLayout
```

![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121629949.png)

#### 显式指定要返回的祖先
```
//*[@text="HK"]/ancestor::android.widget.RelativeLayout[1]
```
>离当前定位元素最近的祖先为1；
>从1开始
## 兄弟姐妹-sibling
### following-sibling
- 选择当前节点之后的所有兄弟节点
##### 节点后有一个兄弟节点
>如果节点后只有一个兄弟节点，则可以用*
```
//*[@text="HK"]/following-sibling::*
```
![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121731170.png)
##### 节点后有多个兄弟节点
```
//*[@resource-id="com.xueqiu.android:id/stock_layout"]/following-sibling::*[@resource-id="com.xueqiu.android:id/price_layout"]
```
![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121736322.png)
### preceding-sibling
- 选择当前节点之前的所有兄弟节点
##### 节点前有一个兄弟节点
>如果节点前只有一个兄弟节点，则可以用*
```
//*[@text="09988"]/preceding-sibling::*
```
![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121737048.png)

##### 节点前有多个兄弟节点

>通过 加自选 元素查找价格元素
```
//*[@resource-id="com.xueqiu.android:id/add_attention"]/preceding-sibling::*[@resource-id="com.xueqiu.android:id/price_layout"]
```

![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121741786.png)


# XPath 运算符
## AND 和 OR
- 可以在 `XPath` 表达式中放置 2 个条件
-   在 `AND` 两个条件都应该为真的情况下，才能找到元素。
-   在 `OR` 的情况下，两个条件中的任何一个为真，就可找到元素。
#### AND
```
//*[@resource-id="com.xueqiu.android:id/current_price" and @text="107.8"]
```
![](https://cdn.jsdelivr.net/gh/testeru-top/images/tester/202207121749776.png)


#### OR
>加自选 在页面上有9个
>前3个元素ID为：`com.xueqiu.android:id/follow_btn`；
>后6个元素ID为：`com.xueqiu.android:id/tv_stock_add_follow`
- 单一定位
```
//*[@resource-id="com.xueqiu.android:id/tv_stock_add_follow"]
```
>只是下面的加自选的元素 页面共6个，上面3个没有查找出来

- `or` 定位获取的是交集
```
//*[@resource-id="com.xueqiu.android:id/tv_stock_add_follow" or @text="加自选"]
```
>加自选的元素都选中出来了 页面共9个

### 总结
- `and` 定位是2个条件的并集
-  `or` 定位是2个条件的是交集