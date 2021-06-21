<template>
  <view class='page progress-page'>
    <DocsHeader title='Progress 进度条' />

    <view class='doc-body'>
      <!--   基础进度条   -->
      <view class='panel'>
        <view class='panel__title'>基础进度条</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtProgress :percent="25" />
          </view>
          <view class='example-item'>
            <AtProgress :percent="50" />
          </view>
          <view class='example-item'>
            <AtProgress :percent="75"/>
          </view>
        </view>
      </view>

      <!--   隐藏进度文案   -->
      <view class='panel'>
        <view class='panel__title'>隐藏进度文案</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtProgress :percent="25" isHidePercent />
          </view>
          <view class='example-item'>
            <AtProgress :percent="75" isHidePercent />
          </view>
        </view>
      </view>

      <!--   自定义进度条线宽   -->
      <view class='panel'>
        <view class='panel__title'>自定义进度条线宽</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtProgress :percent="25" :strokeWidth="6" />
          </view>
          <view class='example-item'>
            <AtProgress :percent="50" :strokeWidth="8" />
          </view>
          <view class='example-item'>
            <AtProgress :percent="75" :strokeWidth="10" />
          </view>
        </view>
      </view>

      <!--   自定义颜色   -->
      <view class='panel'>
        <view class='panel__title'>自定义颜色</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtProgress :percent="25" color='#FF4949' />
          </view>
          <view class='example-item'>
            <AtProgress :percent="50" color='#13CE66' />
          </view>
          <view class='example-item'>
            <AtProgress :percent="75" color='#FFC82C' />
          </view>
        </view>
      </view>

      <!--   不同的状态   -->
      <view class='panel'>
        <view class='panel__title'>不同的状态</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='example-item__desc'>暂停</view>
            <AtProgress :percent="25" />
          </view>
          <view class='example-item'>
            <view class='example-item__desc'>进行中</view>
            <AtProgress :percent="50" status='progress' />
          </view>
          <view class='example-item'>
            <view class='example-item__desc'>错误</view>
            <AtProgress :percent="75" status='error' />
          </view>
          <view class='example-item'>
            <view class='example-item__desc'>已完成</view>
            <AtProgress :percent="100" status='success' />
          </view>
        </view>
      </view>

      <!--   实际案例   -->
      <view class='panel'>
        <view class='panel__title'>实际案例</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtProgress :percent="percent" />
            <view class='example-item__buttons'>
              <view class='btn'>
                <AtButton size='small' :onClick="reduce">
                  <AtIcon value='subtract' :size="12" />
                </AtButton>
              </view>
              <view class='btn'>
                <AtButton size='small' :onClick="increase">
                  <AtIcon value='add' :size="12" />
                </AtButton>
              </view>
            </view>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtProgress, AtButton, AtIcon } from 'taro-ui-vue'

const OFFSET = 15;
export default {
  components: {
    DocsHeader,
    AtProgress,
    AtButton,
    AtIcon
  },
  data() {
    return {
      percent: 0
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    reduce() {
      if (this.percent === 0) {
        return
      }
      this.percent = this.percent - OFFSET < 0 ? 0 : this.percent - OFFSET;
    },
    increase() {
      if (this.percent === 100) {
        return
      }
      this.percent = this.percent + OFFSET > 100 ? 100 : this.percent + OFFSET;
    }
  }
}
</script>
