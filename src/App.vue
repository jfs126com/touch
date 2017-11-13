<template>
  <div id="app">
    <Head/>
    <div class="main">
      <Banner :listImg="listImg"></Banner>
      <!-- <Touch></Touch> -->
      <h1>{{message}}</h1>
      <div class="list">
        <ul>
          <li :class="{active: isbg === index}" v-for="(item,index) in list" @touchstart="start(index)" @touchend="end(index)">{{item}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Head from './components/Head'
import Banner from './components/Banner'
import Touch from './components/Touch'
export default {
  name: 'app',
  data(){
    return{
      listImg:[
        {url:require('../static/banner1.jpg')},
        {url:require('../static/banner2.jpg')},
        {url:require('../static/banner3.jpg')},
        {url:require('../static/banner4.jpg')},
      ],
      list:['App.vue','assets','components','main.js','router','index'],
      isbg:'',
      message:'I am boy'
    }
  },
  components:{
    Head,Banner,Touch
  },
  beforeCreate: function () {             
                console.group('beforeCreate 创建前状态===============》');
               console.log("%c%s", "color:red" , "el     : " + this.$el); //undefined
               console.log("%c%s", "color:red","data   : " + this.$data); //undefined 
               console.log("%c%s", "color:red","message: " + this.message);
               console.log('页面加载中。。。')  
        },
        created: function () {
            console.group('created 创建完毕状态===============》');
            console.log("%c%s", "color:red","el     : " + this.$el); //undefined
               console.log("%c%s", "color:red","data   : " + this.$data); //已被初始化 
               console.log("%c%s", "color:red","message: " + this.message); //已被初始化
               console.log('页面加载完成')
        },
        beforeMount: function () {
            console.group('beforeMount 挂载前状态===============》');
            console.log("%c%s", "color:red","el     : " + (this.$el)); //已被初始化
            console.log(this.$el);
               console.log("%c%s", "color:red","data   : " + this.$data); //已被初始化  
               console.log("%c%s", "color:red","message: " + this.message); //已被初始化  
        },
        mounted: function () {
            console.group('mounted 挂载结束状态===============》');
            console.log("%c%s", "color:red","el     : " + this.$el); //已被初始化
            console.log(this.$el);    
               console.log("%c%s", "color:red","data   : " + this.$data); //已被初始化
               console.log("%c%s", "color:red","message: " + this.message); //已被初始化 
               console.log('请求数据')
        },
        beforeUpdate: function () {
            console.group('beforeUpdate 更新前状态===============》');
            console.log("%c%s", "color:red","el     : " + this.$el);
            console.log(this.$el);   
               console.log("%c%s", "color:red","data   : " + this.$data); 
               console.log("%c%s", "color:red","message: " + this.message); 
        },
        updated: function () {
            console.group('updated 更新完成状态===============》');
            console.log("%c%s", "color:red","el     : " + this.$el);
            console.log(this.$el); 
               console.log("%c%s", "color:red","data   : " + this.$data); 
               console.log("%c%s", "color:red","message: " + this.message); 
        },
        beforeDestroy: function () {
            console.group('beforeDestroy 销毁前状态===============》');
            console.log("%c%s", "color:red","el     : " + this.$el);
            console.log(this.$el);    
               console.log("%c%s", "color:red","data   : " + this.$data); 
               console.log("%c%s", "color:red","message: " + this.message); 
               console.log('你确认删除XX吗？')
        },
        destroyed: function () {
            console.group('destroyed 销毁完成状态===============》');
            console.log("%c%s", "color:red","el     : " + this.$el);
            console.log(this.$el);  
               console.log("%c%s", "color:red","data   : " + this.$data); 
               console.log("%c%s", "color:red","message: " + this.message);
               console.log('当前组件已被删除，清空相关内容')
        },
  methods:{
    start(index){
      this.isbg = index
    },
    end(index){
      this.isbg = false
    }

  }

}
</script>

<style>
html,body,img,ul{margin: 0;padding: 0;}
img{vertical-align: top;}
li{list-style: none;}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
.list ul li{
  padding: 15px 10px;
  font-size: 18px;
  border-bottom: solid 1px #E6E6E6;
  text-align: left;
}
.active{
  background: #E6E6E6;
}
</style>
