<template>
  <div :style="{backgroundImage:'url()'}">
    <div id="todolistapp">
      <div class="container">
        <h1>Todo Vue App</h1>
          <input
          type="input" class="input" placeholder="Name" required v-model="ToDo"
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
              <p class="footer">Build with ❤️ By <a href="https://github.com/AimeneNouri" target="_blank">Aimene Nouri</a> Using <a href="https://vuejs.org/" target="_blank">Vue.js</a></p>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
export default {
  name: "todolistapp",
  data() {
    return {
      ToDo: '',
      ToDoExisting: [
        { name: "Aimene", id: 0 },
        { name: "Ikram", id: 1 },
        { name: "Hassan", id: 2 }
      ]
    }
  },
  methods: {
    add() {
      this.ToDoExisting.push({
        name: this.ToDo,
        id: new Date().valueOf()
      }),
        this.ToDo = ''
    },
    deletetodo(i) {
      this.ToDoExisting.splice(i,1);
    }
  }
};
</script>

<style>
body {
  font-family: 'Rubik', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-size: calc(10px + 0.33vw);
  -webkit-font-smoothing: antialiased;
  padding: 5vh 10vw;
  color: #2c3e50;
}
#todolistapp {
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
  font-size: 20px;
}
input {
  width: 50%;
  padding: 5px 10px;
  margin: 0px 0;
  border: 2px solid #9555af;
  border-radius: 25px;
}
.add-btn {
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
  color: red;
  border-color: currentColor;
  background-color: white;
}
.delete-btn {
  outline: none;
}
.delete-btn::-moz-focus-inner {
  border: none;
}
.footer{
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  font-size: 20px;
  font-weight: bold;
}
a {
  text-decoration: none;
  color: #2c3e50;
  position: relative;
  }
a:after {
  content: "";
  position: absolute;
  z-index: -1;
  top: 60%;
  left: -0.1em;
  right: -0.1em;
  bottom: 0;
  transition: top 200ms cubic-bezier(0, .8, .13, 1);
  background-color: rgb(149, 85, 175, 0.502);
}
a:hover:after {
  top: 0%;
}
</style>
