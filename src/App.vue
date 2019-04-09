<template>
  <div id="app" class="center">
    <div class="card">
      <div class="header center">
        <h2>Todo App</h2>
      </div>

      <input
        v-model="newTodo"
        @keydown.enter="addTodo"
        type="text"
        class="input-text"
        placeholder="add todo item..."
      />

      <ul>
        <todoList
          v-for="todo in todos"
          :key="todo.id"
          :todo="todo"
          @done="completed"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import todoList from "./components/todoList";
let idinit = 0;
export default {
  name: "app",
  components: {
    todoList
  },
  data() {
    return {
      newTodo: "",
      todos: [
        {
          id: idinit++,
          text: "something",
          editMode: false
        },
        {
          id: idinit++,
          text: "something more",
          editMode: false
        }
      ]
    };
  },
  methods: {
    // editTodo: function() {
    //   this.todos = this.todos.map( todo => {

    //   })
    // },

    addTodo: function() {
      var trimmed = this.newTodo.trim();
      if (trimmed)
        this.todos.unshift({ id: idinit++, text: trimmed, editMode: false });
      this.newTodo = "";
    },

    completed: function(id) {
      this.todos = this.todos.filter(todo => {
        return todo.id != id;
      });
    }
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Pacifico|Shadows+Into+Light");

html,
body {
  padding: 0;
  margin: 0;
}

#app {
  font-family: "Shadows Into Light", cursive;
  font-size: 1.2em;
  width: 100vw;
  height: 100vh;
  background-color: cadetblue;
}

.center {
  display: flex;
  justify-content: center;
  align-items: center;
}

.todo {
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;

  p {
    flex: 1;
  }
}
.edit {
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  input {
    box-sizing: border-box;
    width: 100%;
    padding: 6px;
    background: bisque;
    border: 2px solid cadetblue;
    border-radius: 5px;
    transition: all 0.3s ease-in-out;

    &:focus {
      outline: none;
      border-bottom: 2px solid cadetblue;
      background: rgb(253, 241, 226);
    }
  }
}

button {
  font-size: 1.2rem;
  background-color: transparent;
  border: 0;
  height: 60%;
  transition: all 0.3s ease-in-out;

  &:hover,
  &:focus {
    outline: none;
    opacity: 0.6;
    filter: drop-shadow(2px 2px 2px rgba(0, 0, 0, 0.2));
  }
}

.card {
  width: 400px;
  min-height: 80vh;
  border: 5px wheat;
  border-radius: 5px;
  background-color: bisque;
  padding: 10px;
  transition: all 0.3s ease-in-out;
  filter: drop-shadow(4px 4px 4px rgba(0, 0, 0, 0.2));

  .header {
    font-family: "Pacifico", cursive;
    color: #607d8b;
    width: 100%;

    h2 {
      font-size: 2em;
      text-shadow: 2px 2px rgba(0, 0, 0, 0.2);
      margin: 15px;
    }
  }

  .input-text {
    box-sizing: border-box;
    width: 100%;
    padding: 6px;
    background: bisque;
    border: 2px solid cadetblue;
    border-radius: 5px;
    transition: all 0.3s ease-in-out;

    &:focus {
      outline: none;
      border-bottom: 2px solid cadetblue;
      background: rgb(253, 241, 226);
    }
  }

  ul {
    padding: 0 20px;
  }
  li {
    font-size: 1.6em;
    color: #607d8b;
    list-style-type: none;
    display: flex;
    flex-direction: row;
    padding: 5px 0px;
    align-items: center;

    p {
      margin: 0 0 0 10px;
    }
  }
}
</style>
