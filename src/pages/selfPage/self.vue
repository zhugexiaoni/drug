<template>
<<<<<<< HEAD
  <view> This is self page </view>
  <view>
    <AtTabBar fixed :tabList="tabList" @click="handleClickTabList" :current="3" />
  </view>
</template>


<script>
import Taro from '@tarojs/taro'
// 引用全局变量 https://nervjs.github.io/taro-docs/docs/best-practice#全局变量
import { set as setGlobalData, get as getGlobalData } from "../../utils/global_data";

export default {
  name: "selfPage",
  data() {
    return {
      tabList: getGlobalData('tabList')
    };
  },
  methods: {
    handleClickTabList(value) {
      // 跳转到目的页面，在当前页面打开
      Taro.switchTab({
        url: this.tabList[value].url,
      });
    },
    handleClick(value) {
      console.log(value);
    },
  },
};
</script>
=======
  <view class="user">
    <AtAvatar :image="userInfo.avatar" circle 
    @click="navigateTo('/pages/selfInfoPage/selfInfo')">
    </AtAvatar>
    <Text class="nickName" 
    @click="navigateTo('/pages/selfInfoPage/selfInfo')">
    {{userInfo.nickName}}</Text>
    <AtIcon class="setting" value='settings' color='gray' @click="navigateTo('/pages/settingPage/setting')"></AtIcon>
  </view>
  <AtList class="menu" :hasBorder='false'>
    <AtListItem v-for="(item,index) in settingList" :key="index" :title='item.title' arrow='right'
    :thumb='item.icon'
    @click='navigateTo(item.url)'/>
  </AtList>
  <view>
    <AtTabBar fixed :tabList="tabList" @click="handleClickTabList" :current="3" />
  </view>
  <!-- <image src='../../images/用户信息管理.png'></image>
  <image src='../../images/关于.png'></image> -->
  <AtButton class="login" v-if="!userInfo.isLogin" @click="navigateTo('/pages/loginPage/login')">登录</AtButton>
</template>

<script>
  export default {
    name: "selfPage"
  };
</script>

<script setup>
  import "./self.sass";
  import Taro from '@tarojs/taro'
  import {useDidShow} from '@tarojs/taro'
  import { set as setGlobalData, get as getGlobalData } from "../../utils/global_data";
  import { ref } from 'vue'  //ref声明响应式数据

  let userInfo = ref(getGlobalData('userInfo'))
  let tabList = getGlobalData('tabList')
  let settingList = [
    {title:'监护对象管理',url:'/pages/patientsPage/patients',icon:'../../images/用户信息管理.png'},
    {title:'紧急呼救号码管理',url:'/pages/sosPage/sos',icon:'../../images/拨号.png'},
    {title:'关于软件',url:'/pages/aboutPage/about',icon:'../../images/关于.png'}
  ]
  // 更新页面数据
  useDidShow((e) => {
    userInfo.value = getGlobalData('userInfo')
  })
  function handleClickTabList(value) {
    // 跳转到目的页面，在当前页面打开
    Taro.switchTab({
      url: this.tabList[value].url,
    });
  }
  function navigateTo(url,e){
    Taro.navigateTo({url:url})
  }
</script>
>>>>>>> master
