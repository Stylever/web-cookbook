# Retina屏幕下1px边框实现（兼容ios和android）
1px的边框在devicePixelRatio = 2的retina屏下会显示成2px
### 1. 使用 scale(0.5)
需要使用到:after伪元素

	stylus实现：
	border-dpr(style, color, direction = all)
	  & 
	    position relative
	    if direction == all 
	      &:after 
	        content " "
	        width 200%
	        height 200%
	        position absolute
	        top 0
	        left 0
	        border 1px style color
	        -webkit-transform scale(0.5)
	        transform scale(0.5)
	        -webkit-transform-origin 0 0
	        transform-origin 0 0
	        box-sizing border-box
	        pointer-events none    // 解决内部元素无法点击问题
	    else 
	      &:after 
	        content " "
	        position absolute
	        top 0
	        left 0
	        width 200%
	        height 200%
	        border-{direction} 1px style color
	        -webkit-transform scale(0.5)
	        transform scale(0.5)
	        -webkit-transform-origin 0 0
	        transform-origin 0 0
	        box-sizing border-box
	        pointer-events none    // 解决内部元素无法点击问题

### 2. 使用background-image