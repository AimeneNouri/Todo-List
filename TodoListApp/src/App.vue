<template>
  <div id="todolistapp">
    <div class="container">
      <h1>Todo Vue App</h1>
    <input class="input" v-model="ToDo" placeholder="enter a name">
    <button class="add-btn" @click="add()">Add</button>

    <ul style="list-style-type: none;">
    <li v-for="(todo,i) in ToDoExisting">
      <span>
        <strong>{{i + 1}}</strong> => {{  todo.name  }}
      </span>
      <button class="add-btn" @click="deletetodo(i)">Remove</button>
    </li>
    </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'todolistapp',
  data () {
    return {
      ToDo: '',
      ToDoExisting:
      [
        {name: 'Aimene', id:0},
        {name: 'Ikram', id:1},
        {name: 'Hassan', id:2},
      ]
    }
  },
  methods: {
    add(){
      this.ToDoExisting.push({
        name: this.ToDo,
        id: new Date().valueOf()
      }),
      this.ToDo=''
    },
    deletetodo(i){
      this.ToDoExisting.splice(i,1)
    }
  }
}
</script>

<style>

</style>
