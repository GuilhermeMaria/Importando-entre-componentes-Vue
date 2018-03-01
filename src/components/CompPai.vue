<template class="htm">
	<div class="principal">
		<h1> lista de alunos </h1>
		<CompFilho :list="list"
		@remove="value => {remove = value}"
		@removeStudant="value => {removeStudant = value}"></CompFilho>
	</div>
</template>
<script>
import _ from 'lodash'
import CompFilho from './CompFilho.vue'

export default{
	data(){
		return{
			removeStudant: '',
			remove: false,
			configs: {
				orderBy: 'age',
				order: 'desc',
				filter: ''
			},
			alunos: [
				{
					name: 'Guilherme Oliveira',
					age: '16'
				},
				{
					name: 'Cleiton',
					age: '12'
				},
				{
					name: 'Anna Paula',
					age: '25'
				}
			]
		}
	},
	watch: {
		removeStudant(){
			if (this.remove === true) {
				this.list.splice(this.removeStudant, 1)
				this.remove = false
				this.removeStudant = ''	
			}
		}
	},
	computed:{
		list(){
			const filter = this.configs.filter
			const list = _.orderBy(this.alunos, this.configs.orderBy, this.configs.order)

			if (_.isEmpty(filter)) {
				return list
			}

			return _.filter(list, aluno => aluno.name.indexOf(filter) >= 0)
		}
	},
	components: {
		CompFilho
	}
}
</script>
<style scoped>
	
</style>