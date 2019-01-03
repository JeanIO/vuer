<template>
  <div class="container">
		<ul v-if="toDoList.length">
			<template v-for="(item, index) in toDoList">
				<li :key="index" v-if="item.done" @click="changeState(item)"><del>{{item.value}}</del></li>
				<li :key="index" v-else @click="changeState(item)">{{item.value}}</li>
			</template>
		</ul>
	<div>
		<input id="inputPlace"/>
		<button v-on:click="addSomething">add sth</button>
	</div>
	<p><slot name="placement"></slot></p>
	<!-- <p>{{message}}</p>
	<input v-model="message"/> -->
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function(){
		return {
			toDoList: [],
			message: ''

		}
	},
	methods:{
		addSomething: function() {
			let value = document.getElementById('inputPlace').value
			document.getElementById('inputPlace').value = ""
			this.toDoList.push({
				value,
				done: false
			})
		},
		changeState: function(item){
			item.done = true
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
