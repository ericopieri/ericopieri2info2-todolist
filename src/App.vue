<template>
	<div class="structure">
		<Header/>
		<Main @chamadoIndex="taskCheck" @chamadoAddTask="addTask" :tarefas="tarefas"/>
	</div>
</template>

<script>
import Header from '@/components/Header'
import Main from '@/components/Main'

export default {
	components: {Header, Main},
	data() {
		return {
			tarefas: [],
		}
	},
	methods: {
		addTask(newTask) {
			this.tarefas.push({
				nome: newTask,
				checked: false,
			})
		},
		taskCheck(index) {
			if (this.tarefas[index].checked == true) {
				this.tarefas[index].checked = false
			} else {
				this.tarefas[index].checked = true
			}
		}
	}
}
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,400;0,700;1,400;1,700&display=swap');
	* {
		padding: 0;
		margin: 0;
		box-sizing: border-box;
		list-style: none;
		text-decoration: none;
		color: black;
		font-family: 'Poppins', Helvetica, sans-serif;
	}

</style>