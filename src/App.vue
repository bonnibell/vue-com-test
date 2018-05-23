<template>
	<div id="app">
		{{msg}}
		<button @click="showMessage">{{appMsg}}</button>
		<Child v-on:childToParentMsg="showChildToParentMsg"></Child>
		*******************************************************************
		<DisOur v-bind:parentToChild="appMsg">asdfsa</DisOur>
	</div>
</template>

<script>
	var app = require('./app.js')
	import Child from './Chilld.vue'
	import DisOur from './DisOur.vue'
	export default {
		name: 'app',
		data() {
			return {
				msg: '初始化',
				appMsg: '',
				parentMsg:'hehehe'
			}
		},
		methods: {
			showMessage() {
				this.appMsg = app.generateText();
			},
			showChildToParentMsg(data) {
				this.msg = data;
			}
		},
		components: {
			Child,
			DisOur
		}
	}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
	
	h1,
	h2 {
		font-weight: normal;
	}
	
	ul {
		list-style-type: none;
		padding: 0;
	}
	
	li {
		display: inline-block;
		margin: 0 10px;
	}
	
	a {
		color: #42b983;
	}
</style>