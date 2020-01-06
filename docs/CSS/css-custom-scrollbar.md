---
id: css-custom-scrollbar
title: Custom Scrollbar
---

https://codepen.io/stevenlewis/pen/hubpL

#### Always visible scrollbar

```css
body::-webkit-scrollbar {
	-webkit-appearance: none;
}

body::-webkit-scrollbar:vertical {
	width: 11px;
}

body::-webkit-scrollbar:horizontal {
	height: 11px;
}

body::-webkit-scrollbar-thumb {
	border-radius: 8px;
	border: 2px solid white; /* should match background, can't be transparent */
	background-color: rgba(0, 0, 0, 0.5);
}
```
