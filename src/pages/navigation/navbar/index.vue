<template>
  <view class='page'>
    <DocsHeader title='NavBar 导航栏'></DocsHeader>

    <view class='doc-body'>
      <!--   基础用法   -->
      <view class='panel'>
        <view class='panel__title'>基础用法</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtNavBar
              :onClickLeftIcon="this.handleClick.bind(this, '返回')"
              title='NavBar 导航栏示例'
              leftIconType='chevron-left'
            />
          </view>
          <view class='example-item'>
            <AtNavBar
              :onClickLeftIcon="this.handleClick.bind(this, '返回')"
              title='NavBar 导航栏示例'
              leftIconType='chevron-left'
              rightFirstIconType='bullet-list'
              rightSecondIconType='user'
            />
          </view>
          <view class='example-item'>
            <AtNavBar
              :onClickLeftIcon="this.handleClick.bind(this, '返回')"
              title='NavBar 导航栏示例'
              leftIconType='chevron-left'
              rightFirstIconType='user'
            />
          </view>
        </view>
      </view>

      <!--   自定义左上角文案   -->
      <view class='panel'>
        <view class='panel__title'>自定义左上角文案</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtNavBar
              :onClickLeftIcon="this.handleClick.bind(this, '返回')"
              title='NavBar 导航栏示例'
              leftText='返回'
              leftIconType='chevron-left'
              rightFirstIconType='bullet-list'
              rightSecondIconType='user'
            />
          </view>
          <view class='example-item'>
            <AtNavBar
              :onClickLeftIcon="this.handleClick.bind(this, '返回')"
              title='NavBar 导航栏示例'
              leftText='返回'
              rightFirstIconType='bullet-list'
              rightSecondIconType='user'
            />
          </view>
        </view>
      </view>

      <!--   自定义颜色   -->
      <view class='panel'>
        <view class='panel__title'>自定义颜色</view>
        <view class='panel__content no-padding'>
          <AtNavBar
            :onClickRgIconSt="this.clickList.bind(this)"
            :onClickRgIconNd="this.clickMy.bind(this)"
            :onClickLeftIcon="this.clickReturn.bind(this)"
            color='#333'
            title='NavBar 导航栏示例'
            leftText='返回'
            rightFirstIconType='bullet-list'
            rightSecondIconType='user'
          />
        </view>
      </view>

      <!--   自定义图标样式   -->
      <view class='panel'>
        <view class='panel__title'>自定义图标样式</view>
        <view class='panel__content no-padding'>
          <AtNavBar
            :onClickRgIconSt="this.clickList.bind(this)"
            :onClickRgIconNd="this.clickMy.bind(this)"
            :onClickLeftIcon="this.clickReturn.bind(this)"
            color='#333'
            title='NavBar 导航栏示例'
            leftText='返回'
            rightFirstIconType='bullet-list'
            :rightSecondIconType="{ value: 'user', size: 36, color: 'red' }"
          />
        </view>
      </view>

      <!--   无下划线   -->
      <view class='panel'>
        <view class='panel__title'>无下划线</view>
        <view class='panel__content no-padding'>
          <AtNavBar
            :border="false"
            :onClickRgIconSt="this.clickList.bind(this)"
            :onClickRgIconNd="this.clickMy.bind(this)"
            :onClickLeftIcon="this.clickReturn.bind(this)"
            color='#333'
            title='NavBar 导航栏示例'
            leftText='返回'
            rightFirstIconType='bullet-list'
            rightSecondIconType='user'
          />
        </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtNavBar } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

export default {
  components: {
    DocsHeader,
    AtNavBar
  },
  data() {
    return {
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    handleClick(title) {
      Taro.showToast({
        title,
        duration: 2000,
        icon: 'success'
      })
    },
    clickReturn() {
      Taro.showToast({
        title: '返回',
        duration: 2000,
        icon: 'success'
      })
    },
    clickMy() {
      Taro.showToast({
        title: '我的',
        duration: 2000,
        icon: 'success'
      })
    },
    clickList() {
      Taro.showToast({
        title: '功能列表',
        duration: 2000,
        icon: 'success'
      })
    }
  }
}
</script>
