<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([
  { id: id++, text: 'Tugas Pertemuan 1 PBK', done: true },
  { id: id++, text: 'Tugas Pertemuan 2 PBO', done: true },
  { id: id++, text: 'Tugas Pertemuan 1 Matematika Diskrit', done: false }
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <main class="app">
		
		<section class="greeting">
			<h1 class="title"><b>
				<marquee scrolldelay="100" direction="right">WELCOME TO DO WINA TUGAS !</marquee></b>
			</h1><hr><hr>
		</section>
    <section class="create-todo">
			<h3><b>Isi List Tugas Yang Akan di Lakukan!</b></h3>
  <form id="new-todo-form" @submit.prevent="addTodo">
    <input type="text" 
					name="content" 
					id="content" 
					placeholder="Cth : Tugas Pemrograman Berbasis Komponen Pertemuan 1" v-model="newTodo">
    <button class="tugas">Tambahkan Tugas</button>
  </form>
  </section>
  <section class="todo-list">
			<h3><b>LIST TUGAS :</b></h3>
      <div v-for="todo in filteredTodos" :class="`todo-item ${todo.done && 'done'}`">
					<label>
            <ul>
						<input type="checkbox" class="styled-checkbox" v-model="todo.done" >
						<span :class="{ done: todo.done }">{{ todo.text }}</span>
						
			
            </ul>
					</label>

					<div class="todo-content">
						<input type="text" v-model="todo.content" />
					</div>
					
					<div class="actions">
						<button class="delete" @click="removeTodo(todo)">Hapus</button>
					</div>
				</div>
				<div>
				<button class="hide" @click="hideCompleted = !hideCompleted">
   				 {{ hideCompleted ? 'Tampilkan Semua' : 'Sembunyikan yang Selesai' }}
  	</button></div>

		</section>
		
	</main>
	
</template>
<style>
.done {
  text-decoration: line-through;
}
</style>
