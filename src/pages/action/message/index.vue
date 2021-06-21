<template>
  <view class='page toast-page'>
    <DocsHeader title='Message 消息通知' />

    <view class='doc-body'>
      <view class='panel'>
        <view class='panel__title'>基本案例</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton :onClick="this.handleClick.bind(this, '')">
            普通消息
            </AtButton>
          </view>
          <view class='example-item'>
            <AtButton :onClick="this.handleClick.bind(this, 'success')">
            成功消息
            </AtButton>
          </view>
          <view class='example-item'>
            <AtButton :onClick="this.handleClick.bind(this, 'error')">
            错误消息
            </AtButton>
          </view>
          <view class='example-item'>
            <AtButton :onClick="this.handleClick.bind(this, 'warning')">
            警告消息
            </AtButton>
          </view>
          <view class='example-item'>
            <AtButton :onClick="this.handleClick.bind(this, 'info')">
            提示消息
            </AtButton>
          </view>
        </view>
      </view>
    </view>
    <AtMessage />
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtMessage, AtButton } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

export default {
  components: {
    DocsHeader,
    AtMessage,
    AtButton
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
    handleClick(type) {
      Taro.atMessage({
        message: '消息通知',
        type
      });
    }
  }
}
</script>
