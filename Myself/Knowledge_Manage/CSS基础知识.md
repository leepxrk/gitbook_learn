# CSS学习记录 - CSS基础知识



#### CSS基本语法

1. 外部CSS文件通过<link>进行引用；
2. CSS中的选择器对应HTML中各个元素；
3. CSS的基本语法：选择器 + 大括号 + 属性及其赋值，属性通过冒号连接其赋值，多个属性之间需要通过 “;” 进行间隔；
4. 如果属性需要的赋值大于一个单词，则需要加上引号；
5. 可以同时给多个元素进行赋值，给多个元素加上同一个样式需要在不同的选择器之间加上逗号；
6. CSS的继承，未定义的样式的元素会继承其父级元素定义的样式；



**例**

```
//HTML文件
<html>
<head>
	<link href="文件相对路径/test.css" type "text/css" rel="stylesheet">
</head>
<body>
	<H1>一级标题选项</h1>
	<H2>二级标题选项</h2>
	<H3>三级标题选项</h3>
	<H4>四级标题选项</h4>
</body>
</html>
```



```
//CSS文件，文件名为test.css
H1,H2,H3{
    color:red;
    font-family:"sans serif";
}

body{
    color:blue;
    font-family:serif;
}
```



输出

> 一级标题选项（红色字，无衬线字体
>
> 二级标题选项（红色字，无衬线字体
>
> 三级标题选项（红色字，无衬线字体
>
> 四级标题选项（蓝色字，衬线字体

</br></br>



#### CSS选择器

###### 派生选择器

定义：根据元素及其父级元素之间的包含关系定位具体元素；

应用：外层标签和内层标签之间使用 空格 进行连接，添加的标签层级越多定位越准确。



**例**

```
//HTML文件
<html>
<head>
	<meta charset="utf-8">
	<link href="文件相对路径/test1.css" type "text/css" rel="stylesheet">
</head>
<body>
    <p><strong><bdo>测试用文案一</bdo></strong></p>
	<ul>
		<li><strong><bdo>测试用文案二</bdo></strong></li>
		<li>测试用文案三</li>
	</ul>
</body>
</html>
```



```
//CSS文件，文件名为test1.css

li strong bdo{
	color:green;
    font-family:"sans serif";
	font-size: 16px;
}

bdo{
	color:red;
	font-size: 46px;
}

body{
	color: blue;
	font-size: 46px;
    font-family:serif;
}
```



输出

> 测试用文案一（红色46号字，无衬线字体
>
> 测试用文案二（绿色16字，衬线字体
>
> 测试用文案三（蓝色46字，无衬线字体

</br></br>



###### ID选择器





</br></br>



###### 类选择器





</br></br>

###### 属性选择器





