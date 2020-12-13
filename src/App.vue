<template>
  <div id="app">
    <!-- {{ message }}
    <span :title="message">我是span标签</span>
    <div v-for="(item, index) in arr" :key="index">
      {{ item }}
    </div>
    <div v-if="true">我是if指令</div>
    <div v-else-if="false">我是else-if指令</div>
    <div v-else>我是else指令</div>
    <div @click="test">点我</div>
    <input type="text" v-model="text" /> -->
    <!-- <input type="text" v-model.number="first" />
    <select v-model="ope">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    <input type="text" v-model.number="second" />
    <span>={{ result }}</span>
    <div @click="comput">计算</div> -->
    <div v-for="(item, index) in newsList" :key="index">
      <span
        :class="[
          index == 0
            ? 'red'
            : index == 1
            ? 'green'
            : index == 2
            ? 'orange'
            : 'putong',
        ]"
        >{{ index + 1 }}</span
      >{{ item.title }}
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
//() =>  ===  function()

export default {
  name: "App",
  components: {
    // HelloWorld
  },
  data: () => {
    return {
      newsList: [
        { title: "第一条新闻" },
        { title: "第二条新闻" },
        { title: "第三条新闻" },
        { title: "第4条新闻" },
        { title: "第5条新闻" },
        { title: "第6条新闻" },
        { title: "第7条新闻" },
        { title: "第8条新闻" },
      ],
      // first: "",
      // second: "",
      // ope: "+",
      // result: "1",
      // message: "hello",
      // arr: [1, 2, 3, 4, 5],
      // text: "123",
    };
  },
  methods: {
    test() {
      console.log("点击了按钮");
    },
    comput() {
      switch (this.ope) {
        case "+": {
          this.result = parseInt(this.first) + parseInt(this.second);
          break;
        }
        case "-": {
          this.result = parseInt(this.first) - parseInt(this.second);
          break;
        }
        case "*": {
          this.result = parseInt(this.first) * parseInt(this.second);
          break;
        }
        case "/": {
          this.result = parseInt(this.first) / parseInt(this.second);
          break;
        }
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.red {
  color: red;
  font-size: 30px;
}
.green {
  color: green;
  font-size: 30px;
}
.orange {
  color: orange;
  font-size: 30px;
}
.putong {
  color: black;
  font-size: 20px;
}
</style>
