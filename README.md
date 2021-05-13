# Vue guideline for beginer

### 1. Installation
We can install Vue by using script tag or npm. [link]
If you attempt to create new vue project, then create by Vue CLI. [link]

### 2. Introduction:
Vue is a framework to build front-end application and perfectly capable of Single Page Application.
- Versions of vue:
    *	Old version: 1x
    *	Stable version: 2.6.12
    *	Beta new version: 3x
You can find source code on github. [link]
- A component include 3 HTML tags: 
    *	<template>: write HTML code here to create template.
    *	<script>: write js code here follow vue construction.
    *	<style>: write css code here, we have some options like scss, sass, css with scoped or not.
You can split a component into 3 independent files (html, js, css) then import together in another file.
- Important options/ data inside a component:
    *	name: specify name of component.
    *	components: include name of other vue components will be used in the current component. [link]
    *	props: include name of parent’s data is pass through v-bind or attribute to use it in the child component.
    *	mixins: extend of component, can include data, methods, computed, etc. [link]
    *	data declare:
        *	data (object type): declare global variables, can use in entire project.
        *	data() (function type): declare local variables, can access only by current component and child (through props).
    *	computed: a simple operation functions without parameter to solve simple statement.
    *	methods: write custom functions as you want.
    *	watch: to track data changing with output is old and new variable. 

### 3. Template syntax:
- Data binding and directive:
    *	mustache: <p>{{ variable }}</p> to render data of variable, variable can also be computed, methods, statement or ternary expressions. [link]
    *	v-html: <span v-html=”variable”></span> will replace content of <span> with the variable’s value (not recommended). [link]
    *	v-bind: <div v-bind:id=”randomID”></div> to bind value inside of HTML or component tag. [link]
    *	v-model: create two-way binding on a form input element or a component. [link]
    *	v-on: <button v-on:click=”doSomething()”></button> to handle action on click event. [link]
    *	Other directive: v-if, v-for, v-show, etc. [link]
- Shorthand: we can use “:” instead of v-bind and “@” instead of v-on. [link]
- Life cycle hook: 
    *	Built-in function let you call actions in specific life cycle of component. [link]
    *	Diagram: [link]

### 4. Computed:
- Computed is a simplest function without parameter to solve one statement as short as possible. Instead of write a statement inside “mustache” , we can use computed to reuse function and make our code cleaner. [link]
- Computed is same as methods but it only re-evaluate only when some of its reactive dependencies have changed while methods are always re-evaluate. [link] 

### 5. Methods:
Methods as I said, it’s same as computed but can pass parameters into function.

### 6. Watch (or watchers):
Using watcher when you want to track and trace a data (variable) or computed changing. It return old and new data through parameter and you can do your work with it. [link]

Example:
```vue
data(): {
	return {
		message: “hello world”,
	}
}
watch: {
	message: function(newVal, oldVal) {
		// do something with new and old variable
	}
} 
```

### 7. Props:
- Using props to passing data variable from parent to child component with v-bind keyword. [link]

Parent component:
```vue
<template>
	<child-component v-bind:example-name=”name”></child-component>
<template>
<script>
import ChildComponent from “./child-component.vue”;
export default {
	name: “parent-component”,
	components: {
		 ChildComponent
	},
	data() {
		return {
			name: “Nguyen Van A”,
		}
	}
}
</script>
```

Child component:
```vue
<script>
export default {
	name: “child-component”,
	props: {
		exampleName: {
			type: String,
			default: “N/A”
		}
	}
}
</script>
```

- By default, props is one way binding and immutable, it’s mean that you can’t direct change prop data. Instead you need .sync keyword when binding it in parent component to allow mutable it in child component. [link]

### 8. Slot:
- Using slot to serve content to child component from parent component. It’s mean that you can put text, HTML tag, component, etc from parent component to render it inside child component. [link]

- You can naming slots to serve multiple slots. [link]
- Advance topic: scoped-slot can use to receive props from child component to parent component, vice versa data binding. [link]

### 9. Custom events:
- Using when you want use your own event handler, for example: v-on:example-event. [link]
- Advance topic: pass function as a prop [link]

### Reference:
- https://vuejs.org/v2/guide/index.html
- https://cli.vuejs.org/guide/
- https://michaelnthiessen.com/pass-function-as-prop/
