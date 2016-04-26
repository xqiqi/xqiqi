#Issues
记录 Interview 中的一些问题，JavaScript 偏多。

* closed：一般已有解决办法
* open：持续更新



#Code
* demo1：cover-lift

    div 掀起一角的动画效果，基于 CSS3 animation


``` css
#tri{
	position: absolute;
	width: 0;
	height: 0;
	border-radius: 0 0 0 5px;
	border-style: solid;
	border-width: 10px;
	border-color: transparent transparent #e1ca82 #e1ca82;
	top: 0;
	right: 0;
	cursor: pointer;
}

@keyframes transBig{
	0%   {border-width: 10px;}
	50%  {border-width: 55px;}
	100% {border-width: 100px;}
}
@keyframes transSmall{
	0%   {border-width: 100px;}
	50%  {border-width: 55px;}
	100% {border-width: 10px;}
}
```
```javascript
function handleBig (){
	t.style.animation = "transBig 0.5s linear 0s 1 alternate";
	b.style.animation = "transBig 0.5s linear 0s 1 alternate";

	setTimeout(function(){
		t.style.borderWidth = "100px";
		b.style.borderWidth = "100px";
		t.style.animation = null;
		b.style.animation = null;

		t.removeEventListener("click", handleBig, false);
		t.addEventListener("click", handleSmall, false);
	}, 500);
}

function handleSmall (){
	t.style.animation = "transSmall 0.5s linear 0s 1 alternate";
	b.style.animation = "transSmall 0.5s linear 0s 1 alternate";

	setTimeout(function(){
		t.style.borderWidth = "10px";
		b.style.borderWidth = "10px";
		t.style.animation = null;
		b.style.animation = null;

		t.removeEventListener("click", handleSmall, false);
		t.addEventListener("click", handleBig, false);
	}, 500);
}
```
