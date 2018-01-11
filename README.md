# rem.js
适配移动端的rem单位计算
其中的750是根据ui做图的实际尺寸来定，如果在ps上量出的长度是100px，那么转换后是1rem
 ```
(function(doc, win) {//rem引用设置
	var docEl = doc.documentElement,
		resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
		recalc = function() {
			var clientWidth = docEl.clientWidth;
			if(!clientWidth) return;
			if(clientWidth >= 750) {
				docEl.style.fontSize = '100px';
			} else {
				docEl.style.fontSize = 100 * (clientWidth / 750) + 'px';
			}
		};

	if(!doc.addEventListener) return;
	win.addEventListener(resizeEvt, recalc, false);
	doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);
 ```
