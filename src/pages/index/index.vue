<template>
  <view class="page page-index">
    <view class="logo">
      <image :src='logoImg' class='img' />
    </view>
    <view class='page-title'>Taro UI</view>
    <view class='module-list'>
      <view v-for="item in items"
        class='module-list__item'
            @tap="gotoPanel(item.id)"
            :key='item.id'
      >
        <view class='module-list__icon'>
          <image :src='item.icon' class='img' />
        </view>
        <view class='module-list__info'>
          <view class='title'>{{item.title}}</view>
          <view class='content'>{{item.content}}</view>
        </view>
        <view class='module-list__arrow'>
          <view class='at-icon at-icon-chevron-right' />
        </view>
      </view>
    </view>

  </view>
</template>

<script>
// 按需引入, 更小的应用体积
import { AtIcon, AtButton, AtToast, AtNoticebar } from 'taro-ui-vue'
import Taro from '@tarojs/taro'
import "taro-ui-vue/dist/style/components/icon.scss";
import "taro-ui-vue/dist/style/components/button.scss"
import "taro-ui-vue/dist/style/components/toast.scss"
import "taro-ui-vue/dist/style/components/noticebar.scss"
import './index.scss'
export default {
  data () {
    return {
      items: [
        {
          id: 'Basic',
          title: '基础',
          content: '包含颜色、文本、图标等',
          icon: require('../../assets/images/icon-list-basic.png')
        },
        {
          id: 'View',
          title: '视图',
          content: '包含通告栏、标签、徽标等',
          icon: require('../../assets/images/icon-list-view.png')
        },
        {
          id: 'Action',
          title: '操作反馈',
          content: '包含对话框、进度条、动作面板等',
          icon: require('../../assets/images/icon-list-action.png')
        },
        {
          id: 'Form',
          title: '表单',
          content: '包含输入框、单选框、复选框等',
          icon: require('../../assets/images/icon-list-form.png')
        },
        {
          id: 'Layout',
          title: '布局',
          content: '包含列表、浮层、卡片等',
          icon: require('../../assets/images/icon-list-layout.png')
        },
        {
          id: 'Navigation',
          title: '导航',
          content: '包含标签栏、导航栏、分段器等',
          icon: require('../../assets/images/icon-list-navigation.png')
        },
        {
          id: 'Advanced',
          title: '高阶组件',
          content: '包含日历等',
          icon: require('../../assets/images/icon-list-hoc.png')
        }
      ],
      logoImg: require('../../assets/images/logo_taro.png')

    }
  },
  methods: {
    handleClick () {
      this.show = true
    },
    handleClose () {
      this.show = false
    },
    toCustom() {
      this.show = true
      Taro.redirectTo({
        url: '/pages/other/custom'
      })
    },
    gotoPanel(id) {
      console.log("in");
      console.log("navigate to: " + id);
      // Taro.navigateTo({
      //   url: `/pages/panel/index?id=${id.toLowerCase()}`
      // })
    },
    onShareAppMessage() {
      return {
        title: 'Taro UI',
        path: '/pages/index/index',
        imageUrl: 'http://storage.360buyimg.com/mtd/home/share1535013100318.jpg'
      }
    }
  }
    }
</script>
