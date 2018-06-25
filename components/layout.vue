<template>
  <div>
    <div class="app-header">
      <div class="header_box">
        <div class="logo_box">
          <img src="../assets/logo.png" alt="" width="100%" height="100%"/>
        </div>
      <ul class="header_right_box">
        <li>{{username}}</li>
        <li @click="showLog">登录</li>
        <li @click="showReg">注册</li>
        <li @click="showAbout" >关于</li>
      </ul>
      </div>
    </div>
    <div class="app-content">
     <keep-alive>
        <router-view></router-view> 
    </keep-alive>
    </div>
    <div class="app-footer">
      <div class="footer">
       <ul>
        <li>Copyright @ 2018 贵州省党委讲师团</li>
        <li>联系我们    |    联系电话：+86（0851）85508010    |    电子邮箱：gzswjstyjc@163.com</li>
        <li>主办单位：中共贵州省委宣传部    中共贵州省委讲师团       |      黔ICP备11002858号      |     协办单位：北京宣传教育服务中心</li>
       </ul>
    </div>
    </div>
     <my-dialog :is-show="isShowLogDialog" @closeAbout="closeAbout('isShowLogDialog')">
         <logForm @has-login="onSuccessLog"></logForm>
     </my-dialog>
     <my-dialog :is-show="isShowRegDialog" @closeAbout="closeAbout('isShowRegDialog')"><p>reg</p></my-dialog>
     <my-dialog :is-show="isShowAboutDialog" @closeAbout="closeAbout('isShowAboutDialog')"><p>中国教育新闻网是中国教育报刊社主办的以教育新闻为主的网络信息传播平台。它以向社会传播教育的声音，促进教育改革与发展为己任，在保持中国教育报权威性的同时，充分发挥互联网特性，增强吸引力、可读性、亲和力，力求打造成为教育信息网络传播中心。</p></my-dialog>
  </div>
</template>

<script>
import Dialog from "./dialog"
import logForm from "./logForm"
export default {
 // name: 'Layout',
  components:{
    MyDialog:Dialog,logForm
  },
  data () {
    return {
      isShowLogDialog:false,
      isShowRegDialog:false,
       isShowAboutDialog:false,
       username:""
    }
  },
  methods:{
    showAbout() {
        this.isShowAboutDialog=true
    },
    showLog(attr) {
        this.isShowLogDialog=true
    },
    showReg() {
        this.isShowRegDialog=true
    },
    closeAbout(attr) {
        this[attr]=false
    },
    onSuccessLog(data){
        console.log(data);
        this.username=data.username;
    }
  }
}
</script>

<style>
 * {
        box-sizing: border-box;
        text-decoration: none;
    }
    p,ul,li,h1,h2,h3,h4,h5,h6,ol,dl,dd,input,ul,ol,img{
        margin:0;padding:0;list-style:none;border:none;
    }
    body{
        font-weight:normal;
        margin:0;padding:0;list-style:none;color:#000;
        overflow-x: hidden;font-family:"宋体";
    }
    a img{border:none;}
    a{color:#252525;}



   .header_box{
        width:100%;height:100px;background:#333;overflow:hidden;
    }
    .logo_box{
        width:60px;height:60px;float:left;margin-left:30px;margin-top:20px;
    }
    .header_right_box{
        width:auto;height:60px;float:right;margin-right:20px;
    }
    .header_right_box li{
        float:left;height:100px;line-height: 100px;padding:0px 10px;color:#fff;font-weight: 600;cursor: pointer;
    }

     .footer{
        width:100%;height:100px;background:#ccc;
    }
    .footer ul {
        width: 1150px;
        height: 145px;
        margin: 0 auto;
        margin-top: 55px;
    }
    .footer ul li {
        text-align: center;
        color: #666;
        line-height: 30px;
        font-size: 14px;
    }
</style>


