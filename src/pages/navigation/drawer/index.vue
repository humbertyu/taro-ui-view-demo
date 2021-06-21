<template>
  <view class='page'>
    <DocsHeader title='Drawer 抽屉'></DocsHeader>

    <view class='doc-body'>
      <view class='panel'>
        <view class='panel__title'>左边滑出</view>
        <view class='panel__content no-padding'>
          <view class='example'>
            <AtButton :onClick="this.leftDrawerClick.bind(this)">
              显示 Drawer
            </AtButton>
            <AtDrawer
              :show="leftDrawerShow"
              mask
              :onItemClick="onItemClick.bind(this)"
              :onClose="this.onClose.bind(this)"
              :items="['菜单1', '菜单2']"
            ></AtDrawer>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>右边滑出</view>
        <view class='panel__content no-padding'>
          <view class='example'>
            <AtButton :onClick="this.rightDrawerClick.bind(this)">
              显示 Drawer
            </AtButton>
            <AtDrawer
              :show="rightDrawerShow"
              right
              mask
              :onItemClick="this.onItemClick.bind(this)"
              :onClose="this.onClose.bind(this)"
              :items="['菜单1', '菜单2']"
            ></AtDrawer>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>自定义内容</view>
        <view class='panel__content no-padding'>
          <view class='example'>
            <AtButton :onClick="this.childrenDrawerClick.bind(this)">
              显示 Drawer
            </AtButton>
            <AtDrawer
              :show="childrenDrawerShow"
              mask
              :onItemClick="this.onItemClick.bind(this)"
              :onClose="this.onClose.bind(this)"
            >
              <view v-for="(item, index) in childrenItem"
                :class="{
                'drawer-item': true,
                'drawer-item--sub': index === 1 || index === 2
              }"
              @tap="onItemClick(index)"
              :key="`drawer-item-${index}`"
              >
              {{ item }}
              <AtIcon :value="icons[index]" size='20' v-if="index !== 3 && icons[index]" />
              <AtBadge value='3' v-if="index === 3 && icons[index]">
                <AtIcon :value="icons[index]" size='20' />
              </AtBadge>
          </view>
          </AtDrawer>
        </view>
      </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtDrawer, AtButton, AtIcon, AtBadge } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

export default {
  components: {
    DocsHeader,
    AtDrawer,
    AtButton,
    AtIcon,
    AtBadge
  },
  data() {
    return {
      leftDrawerShow: false,
      rightDrawerShow: false,
      childrenDrawerShow: false,
      childrenItem: ['首页', '可自定义结构', '或自定义样式', '消息', '个人'],
      icons: ['home', '', '', 'message', 'user']
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    leftDrawerClick() {
      this.leftDrawerShow = !this.leftDrawerShow;
    },
    rightDrawerClick() {
      this.rightDrawerShow = !this.rightDrawerShow;
    },
    childrenDrawerClick() {
      this.childrenDrawerShow = !this.childrenDrawerShow;
    },
    onItemClick(index) {
      const ENV = Taro.getEnv()
      let content;
      if (typeof index !== 'number') {
        content = ''
      } else {
        content = `你点击了第 ${+index + 1} 个项目`
      }
      if (ENV !== 'WEB') content && Taro.showModal({ content, showCancel: false })
      else content && alert(content)
    },
    onClose() {
      this.leftDrawerShow = false;
      this.rightDrawerShow = false;
      this.childrenDrawerShow = false;
    }
  }
}
</script>
