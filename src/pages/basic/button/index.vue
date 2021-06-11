<template>
  <view class='page'>
    <DocsHeader title='Button 按钮'></DocsHeader>
    <view class='doc-body'>
      <!--   主操作   -->
      <view class='panel'>
        <view class='panel__title'>主操作</view>
        <view class='panel__content'>
          <view class='btn-item'>
            <AtButton
              type='primary'
              onClick={this.onButtonClick.bind(this)}
            >
              主操作按钮
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton
              type='primary'
              loading
              onClick={this.onButtonClick.bind(this)}
            >
              Loading
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton type='primary' disabled>
              不可操作
            </AtButton>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtButton } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtButton
  },
  data() {
    return {
    }
  },
  mounted() {
  },
  methods: {}
}
</script>
