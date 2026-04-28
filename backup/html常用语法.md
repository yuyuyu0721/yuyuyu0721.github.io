
# HTML 日常使用语法指南

## 1. 文档基本结构
```markdown
每个 HTML 文档都需要以下基本结构：

html
<!DOCTYPE html>
<html>
    <body>
        页面内容写在这里
    </body>
</html>
```
* 图例

<img width="497" height="204" alt="Image" src="https://github.com/user-attachments/assets/93e6c0e9-b2a2-4307-b9f9-f668d60d4d08" />

---

## 2. 标题标签

HTML 提供 6 个级别的标题，从大到小：

```html
<h1>这是一级标题（最大）</h1>
<h2>这是二级标题</h2>
<h3>这是三级标题</h3>
<h4>这是四级标题</h4>
<h5>这是五级标题</h5>
<h6>这是六级标题（最小）</h6>
```
* 图例

<img width="579" height="456" alt="Image" src="https://github.com/user-attachments/assets/286b4164-80db-43f8-a133-b8c9e448a08b" />

---

## 3. 段落与文本格式

### 3.1 段落标签 `<p>`

```html
<p>这是一个段落</p>
<p>这是第二个段落。注意：HTML 中的换行和多个空格会被合并为一个空格显示</p>
```
* 图例

<img width="870" height="153" alt="Image" src="https://github.com/user-attachments/assets/def13f97-a933-4f6a-9e3d-fd4c0a578f7b" />

### 3.2 换行标签 `<br>`

```html
<p>这是第三<br>个段落，使用 br 标签可以强制换行</p>
```

<img width="468" height="98" alt="Image" src="https://github.com/user-attachments/assets/a690c07b-15cf-4422-91f3-d85059187e12" />

### 3.3 行内文本标签

| 标签 | 作用 | 示例 |
|:---:|:---|:---|
| `<span>` | 包裹文字，方便操作（行内元素，不独占一行） | `<span>这是一</span>` |
| `<i>` | 斜体 | `<i>斜体文字</i>` |
| `<b>` | 加粗 | `<b>加粗文字</b>` |
| `<u>` | 下划线 | `<u>下划线文字</u>` |

**示例代码：**

```html
<p>这<span>是一</span>个段落</p>
<p>这<i>是一个段落</i>，i 标签使文字变斜体</p>
<p>这<b>是一个段落</b>，b 标签使文字加粗</p>
<p>这<u>是一个段落</u>，u 标签添加下划线</p>
```

<img width="618" height="264" alt="Image" src="https://github.com/user-attachments/assets/06ab0ef0-d9e8-45c9-8e80-9f71c7bf5a2c" />

---

## 4. 容器标签 `<div>`

```html
<div>
    <h1>这是一个标题</h1>
    <p>这是一个段落</p>
</div>
```
>**特点**：块级元素，会独占一行，用于包裹多个元素进行整体操作       
**注意**：<div> 本身没有视觉样式，需要配合 CSS 使用；span与之不同的则是行内元素，不需要独占一行

---

## 5. 图片标签 `<img>`

```html
<img src="图片路径" alt="图片说明文字">
```

**属性说明：**
- `src`：图片的路径（可以是本地路径或网址）
- `alt`：图片无法显示时的替代文字

**示例：**
```html
<img src="https://example.com/image.jpg" alt="这是一张图片">
```

> **提示**：你的本地路径 `file:///` 只能在本地打开，上传到服务器后需要改为相对路径或网址

---

## 6. 链接标签 `<a>`

```html
<a href="链接地址" target="_blank">链接文字</a>
```

**属性说明：**
- `href`：目标网址
- `target`：打开方式
  - `_blank`：在新窗口/标签页打开
  - `_self`：在当前窗口打开（默认）

**示例：**
```html
<基础链接>
<a href="https://www.bilibili.com/">这是B站</a>

<在新窗口打开>
<a href="https://www.bilibili.com/" target="_blank">这是B站（新窗口打开）</a>

<段落中的链接>
<p>若想要在段落中添加链接则可以用 a 标签</p>
```

---

## 7. 列表标签

### 7.1 有序列表 `<ol>`（Ordered List）

```html
<ol>
    <li>第一项</li>
    <li>第二项</li>
    <li>第三项</li>
</ol>
```

**显示效果：**
1. 第一项
2. 第二项
3. 第三项

### 7.2 无序列表 `<ul>`（Unordered List）

```html
<ul>
    <li>苹果</li>
    <li>香蕉</li>
    <li>橙子</li>
</ul>
```

**显示效果：**
- 苹果
- 香蕉
- 橙子

> `<li>`（List Item）是列表项标签，在两种列表中通用

---

## 8. 表格标签 `<table>`

```html
<table border="1">
    <thead>      
        <tr>      
            <th>姓名</th>   
            <th>年龄</th>
            <th>性别</th>
        </tr>
    </thead>
    <tbody>   
        <tr>
            <td>张三</td>  
            <td>18</td>
            <td>男</td>
        </tr>
        <tr>
            <td>李四</td>
            <td>20</td>
            <td>女</td>
        </tr>
    </tbody>
</table>
```

**常用属性：**
- `border="1"`：设置边框宽度为1像素

* 图例
<img width="336" height="165" alt="Image" src="https://github.com/user-attachments/assets/40a2737d-4c89-463b-a4a1-5f6922093340" />

**表格结构说明：**

| 标签 | 全称 | 作用 |
|:---:|:---|:---|
| `<table>` | Table | 创建表格 |
| `<thead>` | Table Head | 表头区域 |
| `<tbody>` | Table Body | 表体区域 |
| `<tr>` | Table Row | 表格行 |
| `<th>` | Table Header | 表头单元格（默认加粗居中） |
| `<td>` | Table Data | 数据单元格 |

---

## 9. 完整示例代码

```html
<!DOCTYPE html>
<html>
<body>
    <div>
        <h1>这是一个标题</h1>
        <p>这<span>是一</span>个段落</p>
        <p>这是第二个段落</p>
        <p>这是第三<br>个段落，使用 br 标签换行</p>
        
        <h2>这是一个二级标题</h2>
        <p>这<i>是一个段落</i>，i 标签斜体</p>
        <p>这<b>是一个段落</b>，b 标签加粗</p>
        <p>这<u>是一个段落</u>，u 标签下划线</p>
    </div>
    
    <h3>这是一个三级标题</h3>
    <img src="image.jpg" alt="这是一张图片">
    
    <h4>这是一个四级标题</h4>
    <a href="https://www.bilibili.com/" target="_blank">这是B站</a>
    
    <h5>这是一个五级标题</h5>
    <ol>
        <li>这是一个有序列表项</li>
        <li>第二个列表项</li>
    </ol>
    
    <ul>
        <li>这是一个无序列表项</li>
        <li>第二个无序列表项</li>
    </ul>
    
    <h6>这是一个六级标题</h6>
    <table border="1">
        <thead>
            <tr>
                <th>姓名</th>
                <th>年龄</th>
                <th>性别</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>张三</td>
                <td>18</td>
                <td>男</td>
            </tr>
        </tbody>
    </table>
</body>
</html>
```

---


## 10. 块级元素 vs 行内元素

| 类型 | 特点 | 代表标签 |
|:---|:---|:---|
| **块级元素** | 独占一行，可设置宽高 | `<div>`、`<p>`、`<h1>`~`<h6>`、`<table>` |
| **行内元素** | 不独占一行，不能设置宽高 | `<span>`、`<i>`、`<b>`、`<u>`、`<a>`、`<img>` |
```
