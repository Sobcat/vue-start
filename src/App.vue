<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->

    <div>{{ message }}</div>
    <!-- 绑定 -->
    <span v-bind:title="message2">
      鼠标悬停几秒查看绑定信息
    </span>
    <!-- 条件 -->
    <p v-if="seen">看到我了</p>
    <!-- 循环 -->
    <ul>
      <li v-for="todo in todos" :key="todo">
        {{todo.text}}
      </li>
    </ul>
    <!-- 反过来 -->
    <p>{{message3}}</p>
    <button v-on:click="reverseMessage">反过来</button>
    <!-- v-model -->
    <p>内容显示：{{message4}}</p>
    <input v-model="message4">
    <!-- 组件 -->
    <ol>
      <todo v-for="item in groceList" v-bind:message5="item" v-bind:key="item.id"></todo>
    </ol>
    
  </div>
</template>

<script>
// 引入组件
import Todo from "./components/todo.vue";

export default {
  name: "app",
  // 组件中 data 必须是一个函数
  data() {
    return {
      message: "Hello Workd!",
      message2: "加载于" + new Date().toLocaleString(),
      seen: true,
      todos: [{ text: "1" }, { text: "2" }, { text: "3" }],
      message3: "fanguolai",
      message4: "xxx",
      groceList: [
        { id: 0, text: "你" },
        { id: 1, text: "我" },
        { id: 2, text: "他" }
      ]
    };
  },
  methods: {
    reverseMessage: function() {
      this.message3 = this.message3
        .split("")
        .reverse()
        .join("");
    }
  },
  components: {
    todo: Todo
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
li {
  list-style: none;
}
</style>
