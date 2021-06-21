<template>
  <view class='page toast-page'>
    <DocsHeader title='Toast 轻提示' />

    <view class='doc-body'>
      <view class='panel'>
        <view class='panel__title'>基本案例</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton
              :onClick="this.handleClick.bind(this, {
              text: '文本内容'
            })"
            >
            文本 Toast
            </AtButton>
          </view>
          <view class='example-item'>
            <AtButton
              :onClick="this.handleClick.bind(this, {
                text: '文本内容',
                icon: 'analytics'
              })"
            >
            文本 + ICON
            </AtButton>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>自定义图片</view>
        <view class='panel__content'>
          <view class='example__item'>
            <AtButton
              :onClick="this.handleClick.bind(this, {
              text: '凹凸实验室',
              image:
              'http://storage.360buyimg.com/mtd/home/group-21533885306540.png'
              })"
            >
            自定义图片 Toast
            </AtButton>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>添加遮罩层</view>
        <view class='panel__content'>
          <view class='example__item'>
            <AtButton
              :onClick="this.handleClick.bind(this, {
              text: '透明遮罩层的作用在于不可点击下面的元素',
              hasMask: true
              })"
            >
            添加遮罩层 Toast
            </AtButton>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>Error Toast</view>
        <view class='panel__content'>
          <view class='example__item'>
            <AtButton
              :onClick="this.handleClick.bind(this, {
              text: '错误提示',
              hasMask: true,
              status: 'error'
              })"
            >
            错误提示 Toast
            </AtButton>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>Success Toast</view>
        <view class='panel__content'>
          <view class='example__item'>
            <AtButton
              :onClick="this.handleClick.bind(this, {
              text: '正确提示',
              hasMask: true,
              status: 'success'
              })"
            >
            正确提示 Toast
            </AtButton>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>Loading Toast</view>
        <view class='panel__content'>
          <view class='example__item'>
            <AtButton
              :onClick="this.handleClick.bind(this, {
              text: '正在加载…',
              hasMask: true,
              status: 'loading'
              })"
            >
            加载中 Toast
            </AtButton>
          </view>
        </view>
      </view>
    </view>

    <AtToast
      :icon="state.icon"
      :text="state.text"
      :image="state.image"
      :status="state.status"
      :hasMask="state.hasMask"
      :isOpened="state.isOpened"
      :duration="state.duration"
      :onClose="handleClose"
    />
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtToast, AtButton } from 'taro-ui-vue'

const INIT_STATE = {
  image: '',
  icon: '',
  text: '',
  duration: 3000,
  hasMask: false,
  isOpened: false
};
export default {
  components: {
    DocsHeader,
    AtToast,
    AtButton
  },
  data() {
    return {
      state: Object.assign({}, INIT_STATE)
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    handleClick(params) {
      if (this.state.isOpened) {
        return;
      }
      this.state = Object.assign({ ...INIT_STATE, isOpened: true }, params);
    },
    handleClose() {
      this.state.isOpened = false;
    }
  }
}
</script>
