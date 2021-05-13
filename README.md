# Vue guideline for beginer

### 1. Installation
* We can install Vue by using script tag or npm. [link](https://vuejs.org/v2/guide/installation.html#NPM)
* If you attempt to create new vue project, then create by Vue CLI. [link](https://cli.vuejs.org/guide/)

### 2. Introduction:
Vue is a framework to build front-end application and perfectly capable of Single Page Application.
* Versions of vue:
    *	Old version: 1x
    *	Stable version: 2.6.12
    *	Beta new version: 3x
You can find source code on github. [link](https://github.com/vuejs/vue)
* A component include 3 HTML tags: 
    *	`<template></template>`: write HTML code here to create template.
    *	`<script></script>`: write js code here follow vue construction.
    *	`<style></style>`: write css code here, we have some options like scss, sass, css with scoped or not.
You can split a component into 3 independent files (html, js, css) then import together in another file.
* Important options/ data inside a component:
    *	name: specify name of component.
    *	components: include name of other vue components will be used in the current component. [link](https://vuejs.org/v2/guide/components-registration.html#Module-Systems)
    *	props: include name of parent’s data is pass through v-bind or attribute to use it in the child component.
    *	mixins: extend of component, can include data, methods, computed, etc. [link](https://vuejs.org/v2/guide/mixins.html#Basics)
    *	data declare:
		*	data (object type): declare global variables, can use in entire project.
        	*	data() (function type): declare local variables, can access only by current component and child (through props).
    *	computed: a simple operation functions without parameter to solve simple statement.
    *	methods: write custom functions as you want.
    *	watch: to track data changing with output is old and new variable. 

### 3. Template syntax:
* Data binding and directive:
    *	mustache: `<p>{{ variable }}</p>` to render data of variable, variable can also be computed, methods, statement or ternary expressions. [link](https://vuejs.org/v2/guide/syntax.html#Text)
    *	v-html: `<span v-html="variable"></span>` will replace content of `<span></span>` with the variable’s value (not recommended). [link](https://vuejs.org/v2/guide/syntax.html#Raw-HTML)
    *	v-bind: `<div v-bind:id="randomID"></div>` to bind value inside of HTML or component tag. [link](https://vuejs.org/v2/guide/syntax.html#Attributes)
    *	v-model: create two-way binding on a form input element or a component. [link](https://vuejs.org/v2/guide/forms.html#Basic-Usage)
    *	v-on: `<button v-on:click="doSomething()"></button>` to handle action on click event. [link](https://vuejs.org/v2/guide/syntax.html#Arguments)
    *	Other directive: v-if, v-for, v-show, etc. [link](https://vuejs.org/v2/api/#Directives)
* Shorthand: we can use `:` instead of v-bind and `@` instead of v-on. [link](https://vuejs.org/v2/guide/syntax.html#Shorthands)
* Life cycle hook: 
    *	Built-in function let you call actions in specific life cycle of component. [link](https://vuejs.org/v2/api/#Options-Lifecycle-Hooks)
    *	Diagram: [link](https://vuejs.org/v2/guide/instance.html#Lifecycle-Diagram)

### 4. Computed:
* Computed is a simplest function without parameter to solve one statement as short as possible. Instead of write a statement inside "mustache" , we can use computed to reuse function and make our code cleaner. [link](https://vuejs.org/v2/guide/computed.html#Basic-Example)
* Computed is same as methods but it only re-evaluate only when some of its reactive dependencies have changed while methods are always re-evaluate. [link](https://vuejs.org/v2/guide/computed.html#Computed-Caching-vs-Methods)

### 5. Methods:
Methods as I said, it’s same as computed but can pass parameters into function.

### 6. Watch (or watchers):
Using watcher when you want to track and trace a data (variable) or computed changing. It return old and new data through parameter and you can do your work with it. [link](https://vuejs.org/v2/guide/computed.html#Watchers)

Example:
```vue
<script>
export default {
    data() {
        return {
            message: "hello world",
        }
    },
    watch: {
        message: function(newVal, oldVal) {
            // do something with new and old variable
        }
    }
}
</script>
```

### 7. Props:
* Using props to passing data variable from parent to child component with v-bind keyword. [link](https://vuejs.org/v2/guide/components-props.html#Passing-Static-or-Dynamic-Props)

Parent component:
```vue
<template>
	<child-component v-bind:example-name="name"></child-component>
</template>
<script>
import ChildComponent from "./child-component.vue";
export default {
	name: "parent-component",
	components: {
		 ChildComponent
	},
	data() {
		return {
			name: "Nguyen Van A",
		}
	}
}
</script>
```

Child component:
```vue
<script>
export default {
	name: "child-component",
	props: {
		exampleName: {
			type: String,
			default: "N/A"
		}
	}
}
</script>
```

* By default, props is one way binding and immutable, it’s mean that you can’t direct change prop data. Instead you need `.sync` keyword when binding it in parent component to allow mutable it in child component. [link](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)

### 8. Slot:
* Using slot to serve content to child component from parent component. It’s mean that you can put text, HTML tag, component, etc from parent component to render it inside child component. [link](https://vuejs.org/v2/guide/components-slots.html#Slot-Content)

* You can naming slots to serve multiple slots. [link](https://vuejs.org/v2/guide/components-slots.html#Named-Slots)
* Advance topic: scoped-slot can use to receive props from child component to parent component, vice versa data binding. [link](https://vuejs.org/v2/guide/components-slots.html#Scoped-Slots-with-the-slot-scope-Attribute)

### 9. Custom events:
* Using when you want use your own event handler, for example: v-on:example-event. [link](https://vuejs.org/v2/guide/components-custom-events.html#Event-Names)
* Advance topic: pass function as a prop [link](https://michaelnthiessen.com/pass-function-as-prop/)

### Reference:
* https://vuejs.org/v2/guide/index.html
* https://cli.vuejs.org/guide/
* https://michaelnthiessen.com/pass-function-as-prop/
