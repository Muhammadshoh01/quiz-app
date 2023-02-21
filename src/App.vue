<template>
	<main>
		<header>The Quiz</header>
		<question
			v-if="currentQuestion < questions.length"
			:question="questions[currentQuestion]"
			@selected-answer="checkResult"
			@select="currentQuest"
		></question>
		<result v-else :count="count"></result>
	</main>
</template>
<script>
import Question from './components/Question.vue'
import Result from './components/Result.vue'

export default {
	components: { Question, Result },
	data() {
		return {
			currentQuestion: 0,
			questions: [
				{
					title: 'What is Vue ?',
					answer: 0,
					selectedOption: null,
					options: ['A framework', 'A library', 'A  programming language'],
				},
				{
					title: 'What is Vuex used for ?',
					answer: 1,
					selectedOption: null,
					options: ['Viewing things', 'State Management', 'Routing pages'],
				},
				{
					title: 'What is Vue Router ?',
					answer: 2,
					selectedOption: null,
					options: [
						'An ice-cream maker',
						'Store Management',
						'A routing library for vue',
					],
				},
			],
			count: 0,
			isTrue: null,
		}
	},
	methods: {
		checkResult(index) {
			if (this.questions[this.currentQuestion].selectedOption != null)
				return false
			this.questions[this.currentQuestion].selectedOption = index
			if (
				this.questions[this.currentQuestion].selectedOption ===
				this.questions[this.currentQuestion].answer
			) {
				this.count++
			}
			console.log(index)
		},
		currentQuest() {
			this.currentQuestion++
		},
	},
}
</script>

<style scoped>
header {
	color: white;
	text-align: center;
	padding-top: 3rem;
	font-size: 3rem;
	font-weight: bold;
}
</style>
