<template>
  <view class='page'>
    <DocsHeader title='Curtain 幕帘'></DocsHeader>

    <view class='doc-body'>
      <AtCurtain
        :isOpened="isOpened"
        :closeBtnPosition="closeBtnPosition"
        :onClose="onClose"
      >
        <image style='width:100%' mode='widthFix' :src="curtainPng" />
      </AtCurtain>

      <!--  顶部关闭  -->
      <view class='panel'>
        <view class='panel__title'>顶部关闭</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton
              :onClick="this.handleChange.bind(this, 'closeBtnPosition', 'top')"
            >
            顶部关闭幕帘
            </AtButton>
          </view>
        </view>
      </view>

      <!--  底部关闭  -->
      <view class='panel'>
        <view class='panel__title'>底部关闭</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton
              :onClick="this.handleChange.bind(
              this,
            'closeBtnPosition',
            'bottom'
            )"
            >
            底部关闭幕帘
            </AtButton>
          </view>
        </view>
      </view>

      <!--  左上关闭  -->
      <view class='panel'>
        <view class='panel__title'>左上关闭</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton
              :onClick="this.handleChange.bind(
              this,
            'closeBtnPosition',
            'top-left'
            )"
            >
            左上关闭幕帘
            </AtButton>
          </view>
        </view>
      </view>

      <!--  右上关闭  -->
      <view class='panel'>
        <view class='panel__title'>右上关闭</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton
              :onClick="this.handleChange.bind(
              this,
            'closeBtnPosition',
            'top-right'
            )"
            >
            右上关闭幕帘
            </AtButton>
          </view>
        </view>
      </view>

      <!--  左下关闭  -->
      <view class='panel'>
        <view class='panel__title'>左下关闭</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton
              :onClick="this.handleChange.bind(
              this,
            'closeBtnPosition',
            'bottom-left'
            )"
            >
            左下关闭幕帘
            </AtButton>
          </view>
        </view>
      </view>

      <!--  右下关闭  -->
      <view class='panel'>
        <view class='panel__title'>右下关闭</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton
              :onClick="this.handleChange.bind(
              this,
            'closeBtnPosition',
            'bottom-right'
            )"
            >
            右下关闭幕帘
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
import { AtButton, AtCurtain } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtButton,
    AtCurtain
  },
  data() {
    return {
      curtainPng: require("../../../assets/images/curtain.png"),
      isOpened: false,
      closeBtnPosition: 'bottom'
    }
  },
  mounted() {
  },
  methods: {
    onClose(event) {
      this.isOpened = false;
    },
    handleChange(stateName, value) {
      this[stateName] = value;
      this.isOpened = true;
    }
  }
}
</script>
