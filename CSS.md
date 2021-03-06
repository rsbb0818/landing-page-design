# CSS 权重

## 样式类型

### 行间

```html
<h1 style="font-size:12px;color:#000;">行间CSS样式</h1>
```

### 内联

```html
<style type="text/css">
  h1 {
    font-size: 12px;
    color: #000;
  }
</style>
```

### 外部

```html
<link rel="stylesheet" href="css/style.css" />
```

## 选择器类型 n 权重计算规则

| 类型                | 样式          | 实例                | 权重      |
| ------------------- | ------------- | ------------------- | --------- |
| !important          |               |                     | 1,0,0,0,0 |
| 内联样式            | style=""      | style="color:#000;" | 1,0,0,0   |
| ID                  | #id           | #content            | 0,1,0,0   |
| 类选择器            | .class        | .content            | 0,0,1,0   |
| 属性选择器          | [type="text"] |                     | 0,0,1,0   |
| 伪类                | :hover        | :hover              | 0,0,1,0   |
| 元素/类型选择器     | p             | div p               | 0,0,0,1   |
| 伪元素              | ::first-line  | ::first-line        | 0,0,0,1   |
| 统配选择器          | \*            | \*                  | 0,0,0,0   |
| 子选择器/相邻选择器 | ...           | >, +                | 0,0,0,0   |

- 继承样式没有权值

## 比较规则

- **1, 0, 0, 0 > 0, 99, 99, 99** 从左往右逐个等级比较, 前一个等级相等才往后比.
- 无论行间, 内部和外部样式, 都按照此规则来比较, 而不是直观比较, 如行间>内部>外部或者 ID>class>元素, 这种错觉是因为行间确实为第一等权重, 所以权重最高, 而内部样式可能写在了外部样式引用了之后, 所以覆盖掉了之前的

## 层叠

在没有`!important`的情况下, 权重相同会比较规则的特殊性, 根据前面的优先级计算规则决定哪条规则起作用; 当特殊性质也一样的时候, css 规则会按顺序排序, 后生命的规则优先级高.

其中 LVHA 原则指的是 :link -> :visited -> :hover -> :active
