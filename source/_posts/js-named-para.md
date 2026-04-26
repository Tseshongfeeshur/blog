---
title: JavaScript 中给函数传入命名参数
date: 2026-04-26 08:16:24
# expires:  # 时效 该时间之后提示文章内容过时

# sticky: 0 # 置顶等级 数字越大越靠前

tags: # 标签列表
    - Web
    - JavaScript
    - 开发
categories: # 分类列表
    - Web

# thumbnail:  # 首页缩略图链接
# cover:  # 页内头图链接
# excerpt:  # 摘要字符串
---

<!--
{% notel 颜色 可选图标 标题 %}
大号笔记块
{% endnotel %}
-->

<!--
{% note success|default|primary|info|warning|danger|tip|question|颜色 可选图标 %}
小号笔记块
{% endnote %}
-->

<!--
{% btn center|regular|large ::按钮::指向链接::可选图标 %}
-->

<!--
{% folding 颜色::标题%}

折叠块

{% endfolding %}
-->

Python 支持这样的写法：

```python
def func(str1 = '0', str2 = 'zero'):
    print(str1 + ' ' + str2)
    return 0

func() # 输出：0 zero
func('1', 'one') # 输出：1 one
func(str2 = 'two') # 输出：0 two
```

Dart 支持这样的写法：

```dart
int func({String str1 = '0', String str2 = 'zero'}) {
    print('$str1 $str2');
    return 0;
}

int main() {
    func(); // 输出：0 zero
    func(str1: '1', str2: 'one'); // 输出：1 one
    func(str2: 'two'); // 输出：0 two
    return 0;
}
```

命名形参语法，使用形参名传入指定形参而不改变其他形参，这在参数列表过长时很有用。

但 JavaScript 并不支持类似的语法。

为了解决这一点，我们可以利用**解构赋值**机制来实现命名形参的传递：

```javascript
function func({ str1 = ‘0’, str2 = 'zero' } = {}) {
  console.log(`${str1} ${str2}`);
  return 0;
}

func(); // 输出：0 zero
func({str1: '1', str2: 'one'}); // 输出：1 one
func({str2: 'two'}); // 输出：0 two
```