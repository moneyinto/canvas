##canvas 学习积累

#####***canvas学习网站***
>[Canvas绘图与动画学习59例](Canvas绘图与动画学习59例)

>[Canvas_Api](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)

#####***canvas小游戏***
>[贪吃蛇](https://jsfiddle.net/moneyinto/zbyysguq/)

1.使用canvas标签
```html
<canvas id="myCanvas" width="200" height="200"></canvas>
```

2.创建canvas画布
```javascript
/*获取canvas元素*/
var canvas = document.getElementById("myCanvas");

/*验证canvas元素是否存在， 浏览器是否支持canvas元素*/
if (!canvas || !canvas.getContext) return false;

/*创建canvas对象*/
var ctx = canvas.getContext("2d")
```
***3d需要引入第三方库，比如[tree.js](https://github.com/mrdoob/three.js)***


3.canvas浏览器支持
> IE支持9以上

>chrome支持10.0以上

>firefox支持3.6以上

>safari支持5.0以上

>opera支持11.0以上

4.canvas基本功能
- 画线

```javascript
/*设置线条的宽度*/
ctx.lineWidth = 10;

/*设置线条的颜色*/
ctx.strokeStyle = 'red';

/*设置线条的起点*/
ctx.moveTo(10,10);

/*设置线条的终点*/
ctx.lineTo(100, 100);

/*设置直线线帽，参数butt，round，square*/
ctx.lineCap = 'butt';

/*根据起点和终点绘制直线*/
ctx.stroke()
```

- 画矩形

```javascript
ctx.lineWidth = 10;
ctx.strokeStyle = 'red';

/*绘制矩形，参数分别为起点坐标x和y，长，宽*/
ctx.strokeRect(10, 10, 100, 60);
/*或*/
ctx.rect(10, 10, 100, 60);
ctx.stroke()

/*绘制实心矩形*/
ctx.fillStyle = 'red';
ctx.fillRect(10, 10, 100, 60)
/*或*/
ctx.rect(10, 10, 100, 60);
ctx.fill()
```

- 画圆

```javascript
ctx.lineWidth = 10;
ctx.strokeStyle = 'red';

/*绘制圆，参数分别为起点坐标x和y，半径，起始角度，终止角度，是否逆时针*/
ctx.arc(100, 100, 70, 0, 2*Math.PI, true);
ctx.stroke()

/*绘制实心圆*/
ctx.fillStyle = 'red';
ctx.arc(100, 100, 70, 0, 2*Math.PI, true);
ctx.fill()
```

- 画圆弧

```javascript
/*绘制圆弧，参数分别是点m坐标x和y，以及点n坐标x和y，圆弧半径*/
ctx.arcTo(120, 10, 120, 50, 40);
ctx.stroke();
```

- 擦除canvas画板

```javascript
/*在实心矩形擦出一个小矩形*/
ctx.fillStyle = 'red';
ctx.fillRect(10, 10, 100, 100);
ctx.clearRect(20, 20, 50, 50);
```

- 画曲线(贝塞尔曲线)
<无>

- 指定绘图区域（clip）

```javascript
ctx.rect(10, 10, 100, 100);

/*指定上方绘制的矩形为下一次绘图的区域，该区域为可是范围，超出的部分将不可视*/
ctx.clip();
```

- 绘制文本

```javascript
/*设置大小和字体*/
ctx.font = '16px Arial';
/*设置内容，参数分别为文本，坐标x和y，文本宽*/
ctx.fillText("hello world", 100, 100, 100); //实心文本

ctx.strokeText("hello world", 100, 100, 100); //空心文本
```

***关于字体设置，可以设置字体的粗细和斜体效果;canvas可以通过textAlign和textBaseline来设置文字的对齐，textAlign是水平方向对齐，值包括center，end，left，right，start，textBaseline是竖直对齐，值包括alphabetic，bottom，hanging，ideographic，middle，top。***

- 绘制图片

```javascript
var img = document.getElementById("**");
img.onload = function () {
	/*从坐标(10， 10)开始绘制整张图片*/
	ctx.drawImage(img, 10, 10);

	/*从坐标(10, 10)开始绘制整张图片，长宽为100*/
	ctx.drawImage(img, 10, 10, 100, 100);

	/*在图片上截取(10, 10)到(100, 100)的部分，将截取部分从(20, 20)开始绘制，长宽为200*/
	ctx.drawImage(img, 10, 10, 100, 100, 20, 20, 200, 200);
}
```