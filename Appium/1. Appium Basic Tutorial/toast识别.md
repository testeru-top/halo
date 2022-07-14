- 一种消息框类型
- 永远不会获得焦点，无法被点击。
- Toast类的思想就是尽可能不引人注意，同时还向用户显示信息，希望他们看到。
- Toast显示的时间有限，Toast会根据用户设置的显示时间后自动消失。
- 是系统级别的控件，属于系统settings
>当app发送消息的时候，不是app自己的弹框，是app发给手机系统，由手机系统进行弹窗，toast空间不在app内，需要特殊的控件识别方法

## 定位
- appium 用的是uiautomator底层来抓取toast，然后再把toast放到控件树内，但是它本身不属于空间。
- 使用的是uiautomator2

- `xpath` 可以找到
```
//*[@class="android.widget.Toast"]

//*[contains(@text,"xxx")]
```
xxx：toast的文本内容


```java
driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(50));  
driver.findElement(AppiumBy.xpath("//*[@class=\"android.widget.Toast\"]"));
```