# Vue Hamburger

A hamburger icon that transitions to a close icon.

![](http://yo.bkwld.com/303I050j2H18/Screen%20Recording%202017-09-05%20at%2001.19%20PM.gif)

## Usage

```javascript
// Add component
import 'vue-hamburger/index.css'
Vue.component('hamburger', require('vue-hamburger'))

// Example Vue component using the hamburger
Vue.component('mobile-nav', {
  data: function() {
    return {
      open: false // The open/close state of the mobile nav
    }
  }
})
```

```html
<mobile-nav>
	<hamburger
		:stroke='2'
		:gap='5'
		color='#192a35'
		:open.sync='open'>
	</hamburger>
</mobile-nav>
```
