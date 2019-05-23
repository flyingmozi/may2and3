<template>
  <div id="app">
    <header class="header">
      <h3>智能证件照</h3>

      <input type="text" placeholder="请输入搜索内容">
    </header>


    <section class="main">
      <div class="nav">

      </div>


      <div class="list">
        <dl v-for="(item,index) in list" :key="index">
          <dt>
            <img :src="item.pic" alt="">
          </dt>
          <dd>
            <h4>{{item.name}}</h4>
            <p>{{item.tit}}</p>
          </dd>
        </dl>
      </div>
    </section>



    <footer class="footer">
      <div class="iconfont icon-shouye"></div>
      <div class="iconfont icon-18"></div>
      <div class="iconfont icon-wode"></div>
    </footer>
  </div>
</template>

<script>

import '../fonts/iconfont.css'
import axios from 'axios'
export default {
  name: 'App',
  components: {
    
  },
  data(){
    return {
      list:[],
    }
  },
  created(){
    axios.post('/api').then(res=>{
      this.list = res.data
      console.log(this.list)
    })
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html,body,#app{
  width:100%;
  height: 100%;
}
#app{
  display: flex;
  flex-direction: column;
}
.header{
  width: 100%;
  height: 44px;
  background: rgb(25, 167, 233);
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.header h3{
  flex: 1;
  text-align: center;
}
.header input{
  width: 50%;
  height: 35px;
  background: rgb(6, 75, 131);
  border: 0;
  color: #fff;
  margin-right: 15px;
  padding-left: 10px;
}
.main{
  width: 100%;
  flex: 1;
}
.footer{
  width: 100%;
  height: 50px;
  display: flex;
  border-top: 1px solid #ccc;
}
.footer div{
  flex: 1;
  text-align: center;
  line-height: 50px;
  font-size: 20px;
}
.nav{
  width: 100%;
  height: 120px;
}
.list{
  width: 100%;
  height: 450px;
  overflow: auto;
  display: flex;
  flex-wrap: wrap;
}
dl{
  width: 50%;
  height:75px;
  display: flex; 
  align-items: center;
  padding: 3px;
}
dl dt{
  width:65px;
  height: 65px; 
}
dt img{
  width: 100%;
  height: 100%;
}
.active{
  color: aqua;
}
</style>
