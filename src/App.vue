<template>
	<SignupForm />
</template>

<script>
import SignupForm from './components/SignupForm.vue';

export default {
	name: 'App',
	components: { SignupForm }

}
</script>

<style>
body {
	background: black;
	color: white;
	padding: 0;
}

#app {
	font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: lightsteelblue;
	margin-top: 60px;
}

form {
	padding: 1rem;
	border: 1px solid rgba(255, 255, 255, .3);
	border-radius: 1rem;
}

label {
	display: block;
}

input[type=text],
input[type=email],
input[type=password] {
	padding: .3rem;
	display: inline-block;

}
</style>
