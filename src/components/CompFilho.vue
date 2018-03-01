<template>
	<section>
		<ul>
			<li v-for="(aluno, index) in list">
				<strong>{{ aluno.name }}</strong>
				<br>
				{{ aluno.age }} anos
				<button v-on:click="removeStudant(index)">X</button>
			</li>	
		</ul>
	</section>
</template>
<script>
	export default{
		name: '',
		props:{
			list: {
				type: Array,
				required:true
			}
		},
		data(){
			return{

			}

		},
		methods:{
			removeStudant(value){
				this.$emit('remove', true)
				this.$emit('removeStudant', value)
			}
		}
	}
</script>
<style scoped>
	
</style>