<template>
  <div>
       <div class="nav-tabbar">
        <img src="../assets/img/logo@2x.png" alt="" id="logo" />
      </div>
    <div class="container"  v-if="haslist" >
      <div id="programe-list">
      <div class="new-programe-list">
          <div class="font-list" @click="hasClick">新建项目</div>
          <div class="search">
            <input type="text" placeholder="搜索项目名称">
              <img src="../assets/img/图层 3 拷贝@2x.png" alt="">
          </div>
          <div class="rank">排列顺序
             <img src="../assets/img/图层 4@2x.png" alt="" @click="changeRank" >
            <div class="rank-class" v-if="defaultRank">
            <span>时间</span>
            <span>名称</span>
          </div>
          </div>
          
      </div>
       <div class="programe-lists">
           <div v-for="(item,index) in programeList ">
             <img src="../assets/img/1.png" alt="">
             <div class="vertical">
                 <p class="title">{{item.programeName}}{{index+1}}
                </p>
                <div class="circle" @click="detailClick(index)">
                  <span></span>
                  <span></span>
                  <span></span>
                </div>
             </div>
              <div class="detailInfo" v-show='currentPrograme==index'>
                <ul>
                  <li>
                    <img src="../assets/img/编辑@2x.png" alt="">
                    <span>编辑</span>
                  </li>
                  
                  <li>
                    <img src="../assets/img/预览@2x.png" alt="">
                    <span>预览</span>
                  </li>
                  
                  <li>
                    <img src="../assets/img/分享@2x.png" alt="">
                    <span>分享</span>
                  </li>
                  
                  <li>
                    <img src="../assets/img/发布@2x.png" alt="">
                    <span>发布</span>
                  </li>
                  
                  <span class="cut-line"></span>

                </ul>
                <ul class="change">
                  <li>重命名</li>
                  <li>建立副本</li>
                  <li class="delete">删除</li>
                </ul>
              </div>
           </div>
         </div>
    </div>
    </div>
    <div class="container" v-else>
      <div  id="miss" >
      <div id="bottom-img">

        <div id="main-image">
          <img src="../assets/img/缺省图@2x.png" />
        </div>
        <div id="new-page" @click="hasClick">
          <div class="font-new">新建项目</div>
        </div>
      </div>
    </div>
    </div>
    <div class="cloak" v-if="newprograme" @click.self="closepop">
       <div id="popup" >
      <span class="text-page">新建项目</span>
      <div class="input-border">
          <input type="text" placeholder="请输入项目名称" />
      </div>
      <div class="line"></div>
      <div class="button-new">
        <div class="font-new">新建项目</div>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      defaultRank:false,
      currentPrograme:null,
      newprograme: false,
      haslist:true,
      programeList:[
           {
            programeImg:'',
            programeName:'项目名称'
             },  
              {
            programeImg:'',
            programeName:'项目名称'
              }, 
                {
            programeImg:'',
            programeName:'项目名称'
             }, 
              {
            programeImg:'',
            programeName:'项目名称'
          },
              {
            programeImg:'',
            programeName:'项目名称'
          },
              {
            programeImg:'',
            programeName:'项目名称'
          },
              {
            programeImg:'',
            programeName:'项目名称'
          },
              {
            programeImg:'',
            programeName:'项目名称'
          },
      ]
    };
  },
 
  methods: {
    hasClick() {
      this.newprograme = true;
      this.isActive = true;
    },
    closepop(){
      console.log("grf")
      this.newprograme=false
    },
    detailClick(index){
      this.currentPrograme=index
    },
    InitPrograme(){
      this.currentPrograme=null
      console.log("sadad")
    },
    changeRank(){
      this.defaultRank=!this.defaultRank
    }

  },
};
</script>

<style>
.rank-class>span{
  cursor: pointer;
  display: block;
  /* display: none; */
}

.rank-class{
  display: block;
  position: absolute;
  
}
.vertical{
  position: relative;
}
.container{
  width:1400px ;
  margin: 0 auto;
  padding-left:60px ;
  padding-top: 40px;
}
.delete{
    color: #EB3535;;
}
.change{
  margin-left: 45px;
  font-size: 18px;
  font-family: Noto Sans S Chinese;
  /* font-weight: bold; */
  color: #333333;
  line-height: 41px;
}
.cut-line{
  /* margin-bottom: 29px; */
  /* margin-top: 20px; */
  display: block;
  margin-bottom: 20px;
  width: 160px;
  height: 1px;
  background: #BFBFBF;

}
.detailInfo li{
  height: 28px;
  margin-bottom: 20px;
}
.detailInfo li>span{
  font-size: 18px;
  line-height: 2px;
}
.detailInfo li>img{
  margin-bottom: -5px;
  display: inline-block;
  padding-right: 20px;
  line-height: 25px;
  width: 20px;
  height: 20px;
}
.detailInfo{
  
  padding: 25px 0 0 28px;
  position: absolute;
  bottom: 40px;
  right:-220px;
  width: 220px;
  height: 360px;
  z-index: 99;
  background: #FFFFFF;
  box-shadow: 0px 7px 16px 0px rgba(191, 191, 191, 0.54);
  border-radius: 15px;
  /* top:0px */
}
.detailInfo>ul{
  list-style: none;
}
.cloak{
  width: 100%;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  background-color:rgba(0,0,0, 0.4);
  z-index: 9999;
}
#programe-list{
  height:100vh ;
}
.circle{
  position: absolute;
  right: 10px;
  top: 10px;
}
.circle>span{
  display: block;
  width: 6px;
  height: 6px;
  margin-top: 5px;
  background: #C0C0C0;
  border-radius: 50%;

}
.title{
  height: 60px;
  position: relative;
  text-align: center;
  /* padding-top:10px ; */
  font-size: 24px;
  font-family: Noto Sans S Chinese;
  color: #333333;
  line-height: 60px;
}
.programe-lists{
  margin-top: 60px !important;
  
  margin: 0 auto;
  float: left;
  
}
.programe-lists>div:nth-child(4n)>{
  
  
}
.programe-lists>div{
  float: left;
  /* margin-bottom: 50px !important; */
  /* display: inline-block; */
  position: relative;
  width: 260px;
  height: 260px;
  margin-left:1px ;
  margin-bottom: 50px;
  margin-right: 117px;
/* margin: 0 30px; */
  /* width: 400px; */
/* height: 400px; */
background: #FFFFFF;
box-shadow: 0px 5px 18px 0px rgba(191, 191, 191, 0.43);
border-radius: 8px;
}
.programe-lists>div:nth-child(4n){
  margin-right: 0px;
}

.programe-lists img{
  display: block;
  margin: 0 auto;
  width: 200px;
  height: 200px;
  border-radius: 8px;
}

.rank{
  position: relative;
  float: right;
  margin-left: 21px;
  width: 200px;
  height: 40px;
  background: #FFFFFF;
  border: 2px solid #BFBFBF;
  border-radius: 30px;
  
  padding-left:23px ;
  font-size: 18px;
  font-family: Noto Sans S Chinese;
  color: #BFBFBF;
  line-height: 42px;

}
.rank >img{
  display: block;
  position: absolute;
  right: 22px;
  top: 16px;
  width: 22px;
  height: 14px;
}

.search{
position: relative;
margin-left:720px ;
float:left;;
width: 200px;
height: 40px;
background: #FFFFFF;
border: 2px solid #BFBFBF;
border-radius: 30px;
}
.search>input{
  margin-left: 25px;
  margin-top:10px ;
  width: 113px;
  height: 18px;
  font-size: 18px;
  font-family: Noto Sans S Chinese;
  color: #BFBFBF;
  line-height: 42px;
  /* width: 100%; */
  background: none;
  outline: none;
  border: none;
  /* color: transparent; */
  text-shadow: 0 0 0 #000;
}
.search>input::-webkit-input-placeholder{
  color: #BFBFBF;
}
.search>img{
  display: block;
  width: 22px;
  height: 25px;
  position: absolute;
  right:17px;
  top:8px
}
.new-programe-list{
  overflow: hidden;
  width: 100%;
  height: 160px;
  position: relative;
  
  
}
.font-list{
  float: left;
  text-align: center;
  letter-spacing: 5px;
  font-size: 24px;
  font-family: Noto Sans S Chinese;
  color: #FFFFFF;
  line-height: 60px;
  width: 200px;
  height: 60px;
  background:#58ADF2;
  box-shadow: 0px 8px 8px 0px rgba(18, 51, 172, 0.54);
  border-radius: 50px;
}

#miss {
  /* display: none; */
  position: relative;
  /* background-color: #FFFFFF; */
  height: 100vh;
  /* opacity: 0.5; */
}
#bottom-img {
}
.nav-tabbar {
  width: 100%;
  height: 60px;
  /* background: #FFFFFF; */
  box-shadow: 0px 9px 8px 0px rgba(89, 173, 242, 0.17);
}
#logo {
  margin-left: 3.1%;
  margin-top: 0.53%;
  width: 135px;
  height: 42px;
}
#main-image {
  margin: 0 auto
}
#main-image>img{
  display: block;
  margin: 0 auto;

}
#new-page {
  position: relative;
  width: 380px;
  height: 100px;
  background: #58adf2;
  box-shadow: 0px 8px 8px 0px rgba(18, 51, 172, 0.54);
  border-radius: 50px;
  margin-left: 40%;
  margin-top: 50px;
}
.font-new {
  position: absolute;
  top: 32px;
  left: 116px;
  display: block;
  width: 147px;
  height: 34px;
  font-size: 36px;
  font-family: Noto Sans S Chinese;
  font-weight: bold;
  color: #ffffff;
  line-height: 41px;
  cursor: pointer;
}
#popup {
  /* display: none; */
  /* position: sticky; */
  position: absolute;
  top: 320px;
  left: 31.45%;
  height: 330px;
  width: 800px;
  height: 420px;
  background: #ffffff;
  border-radius: 30px;
  z-index: 9;
  opacity: 1;
}
.text-page {
  display: block;
  position: absolute;
  left: 326px;
  top: 30.01px;
  width: 147px;
  height: 34px;
  width: 147px;
  /* height: 34px; */
  font-size: 36px;
  font-family: Noto Sans S Chinese;
  font-weight: bold;
  color: #343434;
  line-height: 42px;
}
.input-border{
  width: 720px;
  position: absolute;
  left: 0;
  top:156px;
  left: 250px;

}
#popup input {
  color: #BFBFBF;
  /* text-align: center; */
  /* position: absolute; */
  left: 50%;
  top: 156px;
  display: block;
  width: 100%;
  height: 32px;
  font-size: 30px;
  font-family: Noto Sans S Chinese;
  /* font-weight: bold; */
  /* color: #3b0e0e; */
  line-height: 42px;
  background: none;
  outline: none;
  border: none;
  /* color: transparent; */
  text-shadow: 0 0 0 #000;
}
#popup>input::-webkit-input-placeholder{
  color: #BFBFBF;
}
.line {
  width: 720px;
  height: 2px;
  background: #58aef2;
  position: absolute;
  left: 40px;
  top: 200px;
}
.button-new {
  left: 210px;
  top: 216px;
  position: absolute;
  width: 380px;
  height: 100px;
  background: #58aef2;
  box-shadow: 1px 8px 8px 0px rgba(18, 52, 172, 0.54);
  border-radius: 50px;
}
</style>