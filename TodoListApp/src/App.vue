<template>
  <div id="todolistapp">
    <div class="container">
      <img src="./assets/logo.png" width="75px" height="75px" />
      <h1>Todo Vue App</h1>
      <div class="form__group field">
        <input
          type="input" class="form__field" placeholder="Name" name="name" id="name" required
        />
        <label for="name" class="form__label">Name</label>
      </div>
      <button class="add-btn" @click="add()">Add Todo</button>

      <ul>
        <li v-for="(todo, i) in ToDoExisting">
          <span>
            <strong>{{ i + 1 }}</strong> : {{ todo.name }}
          </span>
          <button class="delete-btn" @click="deletetodo(i)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
export default {
  name: "todolistapp",
  data() {
    return {
      ToDo: "",
      ToDoExisting: [
        { name: "Aimene", id: 0 },
        { name: "Ikram", id: 1 },
        { name: "Hassan", id: 2 }
      ]
    };
  },
  methods: {
    add() {
      this.ToDoExisting.push({
        name: this.ToDo,
        id: new Date().valueOf()
      }),
        (this.ToDo = "");
    },
    deletetodo(i) {
      this.ToDoExisting.splice(i, 1);
    }
  }
};
</script>

<style>
#todolistapp {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size: 1.5rem;
}
h1 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

.delete-btn {
  color: black;
  cursor: pointer;
}

.delete-btn:hover {
  color: red;
}
</style>
