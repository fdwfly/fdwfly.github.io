# fdwfly.github.io
个人主页
<html>
<head>
<meta charset="UTF-8">
<style>
body {
	background: gray;
}
</style>
<script>
$=function(b){return document.getElementById(b)};_=function(){var b,a,f,e={},d=arguments.length;for(var c=0;c<d;c++){b=arguments[c];for(a in b){e[a]=b[a]}}return e};_$=function(){var b,a,e=arguments[0],d=arguments.length;for(var c=1;c<d;c++){b=arguments[c];for(a in e){if(e[a]===undefined||b[a]===undefined)continue;e[a]=b[a]}}return e};
</script>
</head>
<body>
<canvas id=0></canvas>
</body>
<script>
var 场景=$(0).getContext("2d");
_$($(0),{width:900,height:600});
var 计算坐标=function(q){
	return {
		x:q.x+Math.cos(q.a)*q.r,
		y:q.y+Math.sin(q.a)*q.r,
	};
};
var 画=function(q){
	场景.beginPath();
	场景.arc(q.x, q.y, q.r, 0, Math.PI*2, false);
	场景.lineWidth = q.线宽;
	if(q.类型=='圆'){
		场景.fillStyle = q.颜色;
		场景.fill();
	}
	else{
		场景.strokeStyle = q.颜色;
		场景.stroke();
	};
};
var 图={
	x:350,
	y:350,
	r:80,
	颜色:'red',
	线宽:2,
	类型:'圆',
}
var 太阳=_(图);
var 水星=_(图,{r:8,颜色:'blue'});
var 地球=_(图,{r:10,颜色:'yellowgreen'});
var 月亮=_(图,{r:4,颜色:'gold'});
var 土星=_(图,{r:10,颜色:'green'});
var 土卫1=_(图,{r:4,颜色:'gold'});
var 土卫2=_(图,{r:3});
var 水星轨道=_(图,{r:100,颜色:'white',类型:'圈'});
var 地球轨道=_(图,{r:160,颜色:'white',类型:'圈'});
var 月亮轨道=_(图,{r:30,颜色:'white',类型:'圈'});
var 土星轨道=_(图,{r:220,颜色:'white',类型:'圈'});
var 土卫1轨道=_(图,{r:30,颜色:'white',类型:'圈'});
var 土卫2轨道=_(图,{r:20,颜色:'white',类型:'圈'});
var n = 0;
setInterval(function() {
	n++;
	水星转动角度=.003 * n;
	地球转动角度=.001 * n;
	月亮转动角度=.006 * n;
	土星转动角度=.0005 * n;
	土卫1转动角度=.008 * n;
	土卫2转动角度=.01 * n;
	场景.clearRect(0, 0, $(0).width, $(0).height);
	
	画(太阳);
	画(_$(水星,计算坐标(_(水星轨道,{a:水星转动角度}))));
	画(_$(地球,计算坐标(_(地球轨道,{a:地球转动角度}))));
	_$(月亮轨道,{x:地球.x,y:地球.y});
	画(_$(月亮,计算坐标(_(月亮轨道,{a:月亮转动角度}))));
	画(_$(土星,计算坐标(_(土星轨道,{a:土星转动角度}))));
	_$(土卫1轨道,{x:土星.x,y:土星.y});
	画(_$(土卫1,计算坐标(_(土卫1轨道,{a:土卫1转动角度}))));
	_$(土卫2轨道,{x:土星.x,y:土星.y});
	画(_$(土卫2,计算坐标(_(土卫2轨道,{a:土卫2转动角度}))));
	画(水星轨道);
	画(地球轨道);
	画(月亮轨道);
	画(土星轨道);
	画(土卫1轨道);
	画(土卫2轨道);
	
},1);
</script>
</html>
