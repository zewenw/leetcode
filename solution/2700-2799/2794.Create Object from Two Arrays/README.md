# [2794. 从两个数组中创建对象](https://leetcode.cn/problems/create-object-from-two-arrays)

[English Version](/solution/2700-2799/2794.Create%20Object%20from%20Two%20Arrays/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给定两个数组 <code>keysArr </code>和 <code>valuesArr</code>，返回一个新的对象 <code>obj</code>。<code>obj</code> 中的每个键值对都来自 <code>keysArr[i]</code> 和 <code>valuesArr[i]</code>。</p>

<p>- 如果前面的索引中存在重复的键，则应该跳过该键值对。换句话说，只有第一次出现的键会被添加到对象中。</p>

<p>- 如果键不是字符串，则应通过调用 <code>String()</code> 方法将其转换为字符串。</p>

<p>&nbsp;</p>

<p><strong class="example">示例 1：</strong></p>

<pre>
<b>输入：</b>arr1 = ["a", "b", "c"], arr2 = [1, 2, 3]
<b>输出：</b>{"a": 1, "b": 2, "c": 3}
<b>解释：</b>键 "a"、"b" 和 "c" 分别与值 1、2 和 3 配对。
</pre>

<p><strong class="example">示例 2：</strong></p>

<pre>
<b>输入：</b>arr1 = ["1", 1, false], arr2 = [4, 5, 6]
<b>输出：</b>{"1": 4, "false": 6}
<b>解释：</b>首先，将 arr1 中的所有元素转换为字符串。我们可以看到有两个 "1" 的出现。使用第一次出现 "1" 的关联值：4。
</pre>

<p><strong class="example">示例 3：</strong></p>

<pre>
<b>输入：</b>arr1 = [], arr2 = []
<b>输出：</b>{}
<b>解释：</b>没有键，因此返回一个空对象。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>arr1 和 arr2 都是有效的 JSON 数组</code></li>
	<li><code>2 &lt;= JSON.stringify(arr1).length &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>2 &lt;= JSON.stringify(arr2).length &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>arr1.length === arr2.length</code></li>
</ul>

## 解法

<!-- 这里可写通用的实现逻辑 -->

<!-- tabs:start -->

### **TypeScript**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```ts
function createObject(keysArr: any[], valuesArr: any[]): Record<string, any> {
    const ans: Record<string, any> = {};
    for (let i = 0; i < keysArr.length; ++i) {
        const k = String(keysArr[i]);
        if (ans[k] === undefined) {
            ans[k] = valuesArr[i];
        }
    }
    return ans;
}
```

### **JavaScript**

```js
/**
 * @param {Array} keysArr
 * @param {Array} valuesArr
 * @return {Object}
 */
var createObject = function (keysArr, valuesArr) {
    const ans = {};
    for (let i = 0; i < keysArr.length; ++i) {
        const k = keysArr[i] + '';
        if (ans[k] === undefined) {
            ans[k] = valuesArr[i];
        }
    }
    return ans;
};
```

<!-- tabs:end -->
