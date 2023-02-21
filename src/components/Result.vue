<template>
	<div>
		<h1>Congratulations! You answered all questions</h1>
		<p>Your score: {{ count }} out of 3</p>
	</div>
</template>

<script>
export default {
	props: ['count'],
}
</script>

<style scoped>
div {
	text-align: center;
	color: white;
	background: rgb(95, 50, 95);
	width: 50%;
	margin: 0 auto;
	padding: 1rem;
	margin-top: 4rem;
}
</style>
