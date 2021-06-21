<template>
  <view class='page activity-indicator-page'>
    <DocsHeader title='Activity Indicator 活动指示器'></DocsHeader>

    <view class='doc-body'>
      <!--   自定义尺寸   -->
      <view class='panel'>
        <view class='panel__title'>自定义尺寸</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='subitem'>
              <AtActivityIndicator :size="20"></AtActivityIndicator>
            </view>
            <view class='subitem'>
              <AtActivityIndicator :size="24" />
            </view>
            <view class='subitem'>
              <AtActivityIndicator :size="32" />
            </view>
          </view>
        </view>
      </view>

      <!--   自定义颜色   -->
      <view class='panel'>
        <view class='panel__title'>自定义颜色</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='subitem'>
              <AtActivityIndicator color='#13CE66' />
            </view>
            <view class='subitem'>
              <AtActivityIndicator color='#FF4949' />
            </view>
            <view class='subitem'>
              <AtActivityIndicator color='#C9C9C9' />
            </view>
          </view>
        </view>
      </view>

      <!--   自定义文字   -->
      <view class='panel'>
        <view class='panel__title'>自定义文字</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtActivityIndicator content='加载中...' />
          </view>
        </view>
      </view>

      <!--   状态切换   -->
      <view class='panel'>
        <view class='panel__title'>状态切换</view>
        <view class='panel__content '>
          <AtSwitch
            :border="false"
            :title="isOpened ? '开启中' : '关闭中'"
            :checked="isOpened"
            :onChange="handleChange"
          />
          <view class='example-item'>
            <AtActivityIndicator
              content='加载中...'
              :isOpened="isOpened"
            />
          </view>
        </view>
      </view>

      <!--   垂直水平居中   -->
      <view class='panel'>
        <view class='panel__title'>垂直水平居中</view>
        <view class='panel__content'>
          <view class='example-item example-item--center'>
            <AtActivityIndicator mode='center' />
          </view>
          <view class='example-item example-item--center'>
            <AtActivityIndicator mode='center' content='Loading...' />
          </view>
        </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtActivityIndicator, AtSwitch } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtActivityIndicator,
    AtSwitch
  },
  data() {
    return {
      isOpened: true
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    handleChange(value) {
      this.isOpened = value;
    }
  }
}
</script>
