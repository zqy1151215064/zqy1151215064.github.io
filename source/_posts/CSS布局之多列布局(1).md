---
title: CSS布局之多列布局（1）
date: 2021-04-20 10:54:39
tags:
---

# Multicol 的基本概念

多列布局，通常简称为 multicol，是一种用于将内容布局到一组列框（类似于报纸中的列）的规范。

## 关键概念和术语

Multicol 与我们在 CSS 中拥有的其他布局方法不同，它将内容（包括所有后代元素）分成几列。

规范定义的属性是：

- column-width
- column-count
- columns
- column-rule-color
- column-rule-style
- column-rule-width
- column-rule
- column-span
- column-fill
- column-gap

通过向元素添加`column-count`或`column-width`，该元素将成为多列容器，或简称为*Multicol*容器。这些列是匿名框，在规范中成为列框。

## columns 定义

要创建*Multicol*容器，必须使用至少一个`column-*`属性，这些属性为 column-count 和`column-width`。

### column-count 属性

`column-count`属性指定你想要显示内容的列的数量。浏览器会将正确分配的空间给每列并创建需要的列数。

### 示例1：使用 column-count 属性

```html
<div class="container">
  <p>
    Veggies es bonus vobis, proinde vos postulo essum magis kohlrabi welsh onion
    daikon amaranth tatsoi tomatillo melon azuki bean garlic.
  </p>

  <p>
    Gumbo beet greens corn soko endive gumbo gourd. Parsley shallot courgette
    tatsoi pea sprouts fava bean collard greens dandelion okra wakame tomato.
    Dandelion cucumber earthnut pea peanut soko zucchini.
  </p>

  <p>
    Turnip greens yarrow ricebean rutabaga endive cauliflower sea lettuce
    kohlrabi amaranth water spinach avocado daikon napa cabbage asparagus winter
    purslane kale. Celery potato scallion desert raisin horseradish spinach
    carrot soko.
  </p>
</div>
```

```css
.container {
  column-count: 3;
}
```

![column-count](CSS布局之多列布局/column-count.png)

### column-width 属性

`column-width`属性用于给每列设置一个最佳宽度。如果你声明 `column-width`，浏览器将算出该宽度在 *Multicol*容器能分多少列，并且把额外的空间填充到这些列当中。因此，应将列框视为最小宽度，因为由于额外的空间，列可能而更宽。

### 示例2：使用 column-width 属性

在以下示例中，我们使用 column-width 属性值为 200 px。但最终为了适配容器，列的宽度却大于 200 像素，额外的空间被平均分配了。

```html
<div class="container">
  <p>
    Veggies es bonus vobis, proinde vos postulo essum magis kohlrabi welsh onion
    daikon amaranth tatsoi tomatillo melon azuki bean garlic.
  </p>

  <p>
    Gumbo beet greens corn soko endive gumbo gourd. Parsley shallot courgette
    tatsoi pea sprouts fava bean collard greens dandelion okra wakame tomato.
    Dandelion cucumber earthnut pea peanut soko zucchini.
  </p>

  <p>
    Turnip greens yarrow ricebean rutabaga endive cauliflower sea lettuce
    kohlrabi amaranth water spinach avocado daikon napa cabbage asparagus winter
    purslane kale. Celery potato scallion desert raisin horseradish spinach
    carrot soko.
  </p>
</div>
```

```css
.container {
  column-width: 200px;
}
```

![column-width](CSS布局之多列布局/column-width.png)

### 同时使用 column-count 和 column-width

如果在 *multicol*容器上指定这两个属性，则 `column-count`将作为最大列数。因此，将按 `column-width`的值计算，直到达到 `column-count`定义的列数。在此之后，即使有足够的空间容纳指定列宽大小的列，也不会再绘制，并且额外空间在现有列之间均匀分布。

### 示例3

```html
<div class="container">
  <p>
    Veggies es bonus vobis, proinde vos postulo essum magis kohlrabi welsh onion
    daikon amaranth tatsoi tomatillo melon azuki bean garlic.
  </p>

  <p>
    Gumbo beet greens corn soko endive gumbo gourd. Parsley shallot courgette
    tatsoi pea sprouts fava bean collard greens dandelion okra wakame tomato.
    Dandelion cucumber earthnut pea peanut soko zucchini.
  </p>

  <p>
    Turnip greens yarrow ricebean rutabaga endive cauliflower sea lettuce
    kohlrabi amaranth water spinach avocado daikon napa cabbage asparagus winter
    purslane kale. Celery potato scallion desert raisin horseradish spinach
    carrot soko.
  </p>
</div>
```

```css
.container {
  column-count: 2;
  column-width: 200px;
}
```

![column-count_and_column-width](CSS布局之多列布局/column-count_and_column-width.png)

### columns 缩写

可以使用 `columns`缩写来设置 `column-count`和 `column-width`。如果设置长度单位，这将用于 `column-width`，设置一个整数，它将用于 `column-count`。可以设置两者，用空格分隔这两个值。`columns`可以按任意顺序将属性指定为下面列出的一个或两个值。

此 CSS 结果与示例1相同，column-count 设置为3。

```css
.container{
  columns: 3;
}
```

此CSS结果与示例2相同，column-width 为200px。

```css
.container{
  columns: 200px;
}
```

此CSS结果与示例3相同，同时设置column-count和column-width。

```css
.container{
  columns: 2 200px;
}
```



