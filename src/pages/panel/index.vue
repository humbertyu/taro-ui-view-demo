<template>
  <view class='page'>
    <view class='panel-header'>
      <view class='panel-header__icon'>
        <image v-if="icon" src={icon} class='img' mode='widthFix' />
        <text v-else class='at-icon at-icon-list' />
      </view>
      <view className='panel-header__title'>{title}</view>
    </view>
  </view>
</template>
<script>
import Taro from "@tarojs/taro";
import './index.scss'


export default {
  data() {
    return {
      // panelNames: {
      //   basic: {
      //     name: '基础',
      //     icon: iconBasic
      //   },
      //   view: {
      //     name: '视图',
      //     icon: iconView
      //   },
      //   action: {
      //     name: '操作反馈',
      //     icon: iconAction
      //   },
      //   form: {
      //     name: '表单',
      //     icon: iconForm
      //   },
      //   layout: {
      //     name: '布局',
      //     icon: iconLayout
      //   },
      //   navigation: {
      //     name: '导航',
      //     icon: iconNavigation
      //   },
      //   advanced: {
      //     name: '高阶组件',
      //     icon: iconHOC
      //   }
      // },
      icon: "",
      title: "",
      items: [
        {
          id: 'Basic',
          title: '基础',
          content: '包含颜色、文本、图标等',
          // icon: require('../../assets/images/icon-list-basic.png')
        }
      ],
    }
  },
  mounted() {
    let currentId = Taro.getCurrentInstance().router.params.id;
    // this.title = (this.panelNames[currentId] && this.panelNames[currentId].name) || '';
    // this.icon = (this.panelNames[currentId] && this.panelNames[currentId].icon) || '';
  },
  methods: {

  }
}
</script>
