<template>
  <div>
    <header>
      <div class="header-title">Vue Trello?</div>
    </header>
    <div class="main-container" id="app">
      <div class="list-container">
        <div class="list-header">買い物リスト</div>
        <div class="cards-container">
          <!-- WORKで編集するのはここから👇 -->
          <div class="card" v-for="(todo, i) in list" v-bind:key="i">
            <input type="checkbox" v-model="todo.isDone" />
            <div class="text" v-bind:class="{ centerline: todo.isDone }">
              {{ todo.text }}
            </div>
            <div class="delete" @click="deleteTodo(i)"></div>
          </div>
          <!-- WORKで編集するのはここまで👆 -->
        </div>
        <div class="list-footer">
          <div class="input-container">
            <!-- WORKで編集するのはここから👇 -->
            <input type="text" class="input-todo" v-model="inputTodo" />
            <div class="input-button" @click="addTodo">追加</div>
            <!-- WORKで編集するのはここまで👆 -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      list: [
        { text: "ひき肉を300g買う", isDone: false },
        { text: "ホウレンソウを1束買う", isDone: false },
        { text: "ピーマンを2個買う", isDone: false },
      ],
      inputTodo: "",
    }
  },
  // ここでは複数記述していた処理をまとめている
  watch: {
    list: {
      handler: function () {
        localStorage.list = JSON.stringify(this.list)
      },
      deep: true,
    },
  },
  created: function () {
    if (localStorage.list) {
      this.list = JSON.parse(localStorage.list)
    }
  },
  methods: {
    addTodo: function () {
      const obj = { text: this.inputTodo, isDone: false }
      this.list.push(obj)
    },
    deleteTodo: function (i) {
      this.list.splice(i, 1)
    },
  },
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  overflow: hidden;
}
header {
  position: absolute;
  top: 0px;
  width: 100%;
}
.header-title {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 40px;
  font-size: 1.5em;
  background-color: #0064a5;
  color: #7fb1d2;
}
.main-container {
  display: flex;
  flex-wrap: nowrap;
  align-items: flex-start;
  height: 100vh;
  padding: 52px 12px 12px 12px;
  overflow-x: auto;
  background-color: #0076c2;
}
.list-container {
  min-width: 250px;
  width: 250px;
  padding: 8px;
  border-radius: 4px;
  background-color: #e2e4e6;
}
.list-container:nth-child(n + 2) {
  margin-left: 8px;
}
.list-header {
  height: 60px;
  padding: 8px 0px 0px 4px;
  font-weight: bold;
  font-size: 0.9em;
}
.cards-container {
  max-height: calc(100vh - 200px);
  margin-top: 4px;
  overflow-y: auto;
}
.card {
  display: flex;
  align-items: center;
  position: relative;
  padding: 4px;
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 1px 0 #ccc;
}

.card:nth-of-type(n + 2) {
  margin-top: 8px;
}
.card:last-child {
  margin-bottom: 1px;
  word-wrap: break-word;
}
.card .text {
  overflow-x: hidden;
}
.card input {
  margin-right: 0.5rem;
}
.card:hover {
  background-color: #edeff0;
  border-bottom-color: #d6dadc;
}
.card:hover .delete {
  position: absolute;
  bottom: 4px;
  right: 4px;
  z-index: 16;
  opacity: 0.5;
  color: #f00;
}
.card:hover .delete:after {
  content: "削除";
}
.card:hover .delete:hover {
  opacity: 1;
}

.input-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.input-container .input-todo {
  height: 2em;
  width: 75%;
  padding: 4px;
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 1px 0 #ccc;
  font-size: 1em;
  border-width: 0px;
}
.input-container .input-todo:focus {
  outline: 0;
}
.input-container .input-button {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 30px;
  padding: 0px 0.5em;
  color: #fff;
  background-color: #2ab643;
  border-radius: 4px;
  border-bottom: 1px solid #2aa138;
  user-select: none;
}
.input-container .input-button:active {
  transform: translateY(2px);
}
.list-footer {
  margin-top: 8px;
}

.centerline {
  text-decoration: line-through;
}
</style>
