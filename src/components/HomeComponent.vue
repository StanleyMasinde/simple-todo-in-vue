<template>
  <main class="content">
    <div class="to-do">
      <h1>To do App</h1>
      <form @click.prevent action="#" method="post">
        <input autofocus type="text" placeholder="Add Item" v-model="item" />
        <button type="submit" @click.prevent="addItem(item)">Add Item</button>
        <button data-role="reorder" @click.prevent="reorder">Reorder</button>
      </form>
    </div>

    <div
      draggable="true"
      @dblclick="removeItem(todo)"
      v-for="todo in todos"
      :key="todo"
      class="to-do-list"
    >{{ todo }}</div>
  </main>
</template>

<script>
export default {
  data: function() {
    return {
      item: null,
      todos: ["eat", "cook", "go"]
    };
  },
  methods: {
    addItem(item) {
      if (!item) {
        return;
      }
      this.todos.push(item);
      this.item = null;
    },
    removeItem(item) {
      var it = this.todos;
      var toRemove = it.indexOf(item);
      it.splice(toRemove, 1);
    },
    reorder() {
      this.todos.reverse()
    }
  }
};
</script>

<style>
div.to-do {
  text-align: center;
}
div.to-do,
div.to-do-list {
  border: 2px solid;
  padding: 15px;
  border-radius: 15px 0px 15px 0px;
  box-shadow: -2px 2px 14px black;
}
div.to-do > form > input {
  border: 2px solid;
  padding: 15px;
  border-radius: 15px 0px;
}
form > button {
  padding: 15px;
  margin: 10px;
  border-radius: 15px 0;
  border: 2px solid;
}
.to-do-list {
  margin-top: 15px;
  text-transform: capitalize;
}
div.to-do-list:last-of-type {
  border-radius: 0px 0px 15px 15px;
}
div.to-do-list:first-of-type {
  border-radius: 0px 0px 0px 0px;
}
main.content {
  display: flex;
  display: -webkit-flex;
  align-content: center;
  flex-wrap: wrap;
  justify-content: center;
}

@media screen and (min-width: 585px) {
  div.to-do,
  .to-do-list {
    width: 60%;
  }
}
@media screen and (max-width: 584px) {
  div.to-do,
  .to-do-list {
    width: 100%;
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
