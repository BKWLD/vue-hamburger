# Vue Hamburger

A hamburger icon that transitions to a close icon.

![](http://yo.bkwld.com/303I050j2H18/Screen%20Recording%202017-09-05%20at%2001.19%20PM.gif)

## Usage

```javascript
import 'vue-hamburger/index.css'
VueHamburger = import 'vue-hamburger'
Vue.component('hamburger', VueHamburger)
```

```html
<header>
	<hamburger
		:stroke='2'
		:gap='5'
		color='#192a35'
		:open.sync='open'>
	</hamburger>
</header>
```
