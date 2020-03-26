<template>
  <div id="todolistapp">
    <div class="container">
      <h1>Todo Vue App</h1>
        <input
        type="input" class="input" placeholder="Name" required
        />
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
input {
  width: 50%;
  padding: 5px 10px;
  margin: 0px 0;
  border: 2px solid #9555af;
  border-radius: 25px;
}
.add-btn {
  /* default for <button>, but useful for <a> */
  display: inline-block;
  text-align: center;
  text-decoration: none;
  /* create a small space when buttons wrap on 2 lines */
  margin: 2px 0;
  /* invisible border (will be colored on hover/focus) */
  border: solid 1px transparent;
  border-radius: 4px;
  /* size comes from text & padding (no width/height) */
  padding: 0.5em 1em;
  /* make sure colors have enough contrast! */
  color: #ffffff;
  background-color: #9555af;
  border-radius: 25px;
}
.add-btn:hover {
  color: #9555af;
  border-color: currentColor;
  background-color: white;
}
.add-btn {
  outline: none;
}
.add-btn::-moz-focus-inner {
  border: none;
}
.delete-btn {
  display: inline-block;
  text-align: center;
  text-decoration: none;
  margin: 2px 0;
  border: solid 1px transparent;
  border-radius: 4px;
  padding: 0.5em 1em;
  color: #ffffff;
  background-color: #9555af;
  border-radius: 25px;
}
.delete-btn:hover {
  color: #fff;
  border-color: currentColor;
  background-color: red;
}
.delete-btn {
  outline: none;
}
.delete-btn::-moz-focus-inner {
  border: none;
}
</style>
