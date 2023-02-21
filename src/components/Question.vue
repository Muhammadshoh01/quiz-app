<template>
	<section class="question">
		<div class="answers">
			<h2>{{ question.title }}</h2>
			<p
				v-for="(answer, index) in question.options"
				:key="index"
				@click="$emit('selected-answer', index)"
				:class="{
					true: index == question.answer && question.selectedOption != null,
					false:
						question.selectedOption != question.answer &&
						index == question.selectedOption,
				}"
			>
				{{ answer }}
			</p>
		</div>
		<button
			:disabled="question.selectedOption == null"
			@click="$emit('select')"
		>
			Select an option
		</button>
	</section>
</template>

<script>
export default {
	props: ['question'],
}
</script>

<style scoped>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
html {
	font-family: sans-serif;
}
main {
	width: 100%;
	height: 100%;
}

.question {
	width: 50%;
	height: auto;
	margin: 0 auto;
	background: rgb(95, 50, 95);
	padding: 1rem;
	margin-top: 3rem;
}
.answers p {
	background: #220722;
	padding: 1rem;
	border-radius: 5px;
	margin-bottom: 1rem;
	color: rgb(226, 205, 177);
	cursor: pointer;
}
h2,
span {
	color: rgba(255, 255, 255, 0.5);
	margin-bottom: 1rem;
}
.title {
	margin-bottom: 1rem;
}
button {
	background: rgb(49, 194, 49);
	color: #220722;
	font-size: 1.5rem;
	padding: 0.75rem;
	border-radius: 8px;
	border: none;
	cursor: pointer;
}
button:disabled {
	background: rgb(72, 124, 72);
	cursor: not-allowed;
}
.answers p.true {
	background-color: rgb(49, 158, 49);
}
.answers p.false {
	background-color: red;
}
</style>
