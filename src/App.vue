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
    <!-- <div v-for="(item, index) in newsList" :key="index">
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
    </div> -->
    <!-- <div class="random">
      <input type="text" v-model="name">
      <button @click="add" :disabled="this.name==''">添加</button>
      <button @click="suiji" :disabled="this.arr.length==0">随机</button>
      <button @click="stopp" :disabled="this.arr.length==0">停</button>
      <div class="shuzu">
        <h2 v-if="!this.arr.length==0">添加的所有数据</h2>
        <span v-for="(item,index) in arr" :key="index">
          {{item}}
        </span>
      </div>
      <div class="shuzu">
        <h2 v-if="!this.arr.length==0">随机数据</h2>
        {{arr1}}
      </div>
    </div> -->
    <div class="friend" v-if="shown">
      <div class="header">
        <div @click="openn" class="camera">相机</div>
        <p class="name">王嘉磊</p>
        <div class="img"></div>
      </div>
      <div class="contain">
        <div class="item" v-for="(item, index) in fri" :key="index"> 
          <div class="item_left">
            <img class="headxiang" :src="item.head" alt="">
          </div>
          <div class="item_right">
            <div class="frititle">{{item.name}}</div>
            <div class="fritext">{{item.text}}</div>
            <div v-if="!item.pic==''" class="pics">
              <img class="pic" :src="item.pic" alt="">
              <!-- <img class="pic" src="./assets/logo.png" alt="">
              <img class="pic" src="./assets/logo.png" alt=""> -->
            </div>
            <div class="fabutime">
              {{item.time}}
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="send" v-if="!shown">
      <div class="fabu_head">
        <span>取消</span>
        <span :disabled="[!xiangfa=='']" :class="[!xiangfa==''?'fabubtn':'fabubtn1']" @click="fabu">发布</span>
      </div>
      <div>
        <textarea 
          v-model="xiangfa"
          class="kuang" 
          cols="30" 
          rows="10" 
          placeholder="这一刻的想法..."></textarea>
      </div>
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
      xiangfa:'',
      shown:true,
      fri:[
        {
          head:require('./assets/img/head.jpg'),
          name:'马云',text:'今天的成果',
          pic:require('./assets/img/name.jpg'),
          time:'2小时前'
        },
        {
          head:require('./assets/img/head.jpg'),
          name:'马云',text:'今天的成果',
          // pic:require('./assets/img/name.jpg'),
          time:'2小时前'
        },
      ],
      name:'',
      arr:[],
      arr1:'',
      start:'',
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
    fabu(){
      if(this.xiangfa!=''){
        this.fri.unshift({head:require('./assets/img/head.jpg'),
          name:'我',text:this.xiangfa,
          time:'刚刚'})
      console.log(this.fri)
      this.xiangfa=''
      this.shown=true
      }
      
    },
    openn(){
      this.shown=false
    },
    add(){
      this.arr.push(this.name)
      this.name=''
      console.log(this.arr)
    },
    suiji(){
      this.start=setInterval(() => {
        this.arr1=this.arr[Math.floor(Math.random() * this.arr.length)]
      }, 300);
    },
    stopp(){
      clearInterval(this.start)
    },
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
.header {
      width: 100%;
      height: 250px;
      background: yellowgreen;
      position: relative;
    }

    .name {
      position: absolute;
      bottom: -15px;
      right: 130px;
      font-size: 20px;
      color: white;
    }

    .img {
      width: 100px;
      height: 100px;
      background: orange;
      position: absolute;
      bottom: -50px;
      right:25px;
      border-radius: 15px;
    }
    .camera {
      width: 60px;
      height: 60px;
      background: #ffffff;
      position: absolute;
      right: 10px;
      top: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .contain{
      width: 100%;
      height: auto;
      /* background: chocolate; */
      padding-top: 50px;
    }
    .item{
      padding-top: 30px;
      width: 100%;
      height: auto;
      /* background: rgb(133, 145, 145); */
      display: flex;
      flex-direction: row;
      border-bottom: 1px solid rgb(133, 145, 145);
    }
    .item_left{
      width: 15%;
      height: auto;
      margin-right: 20px;
    }
    .headxiang{
      width: 60px;
      height: 60px;
      
    }
    .item_right{
      display: flex;
      flex-direction: column;
    }
    .frititle{
      font-size: 25px;
      color: rgb(30, 63, 211);
    }
    .fritext{
      margin-top: 6px;
      font-size: 20px;
    }
    .pics{
      display: flex;
      margin-top: 10px;
    }
    .pic{
      width: 100px;
      height: 100px;
      margin-right: 5px;
    }
    .fabutime{
      margin-top: 20px;
      height: 50px;
      color: rgb(216, 209, 209);
    }
    .send{
      width: 100%;
      height: 50px;
      /* background: orange; */
    }
    .fabu_head{ 
      width: 100%;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .fabubtn{
      background: rgb(30, 247, 138);
      padding: 5px;
      border-radius: 5px;
      cursor: pointer;
    }
    .fabubtn1{
      background: rgb(153, 172, 163);
      padding: 5px;
      border-radius: 5px;
      cursor: not-allowed;
    }
    .kuang {
      border: none;
      width:100%;
      height: 300px;
      /* padding-left: 20px; */
      font-size: 30px;
    }
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
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
.shuzu{
  width: 500px;
  height: 250px;
  border: 1px solid red;
  margin: 10px auto;
}
</style>
