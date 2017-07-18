<template>
	<div id="app">
		<router-view></router-view>
	</div>
</template>

<script>
export default {
	name: 'app'
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Cabin');

body {
	background: linear-gradient(to bottom right, #f09, #0f9);
	min-height: 100vh;
}

#app {
	font-family: 'Cabin', 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;

	padding: 2rem;
}
</style>
