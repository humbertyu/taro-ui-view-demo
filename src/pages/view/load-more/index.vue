<template>
<view class='page'>
  <DocsHeader title='LoadMore 页面提示'></DocsHeader>

  <view class='doc-body'>
    <!--   文字   -->
    <view class='panel'>
      <view class='panel__title'>一般用法</view>
      <view class='panel__content no-padding'>
        <AtLoadMore
          :onClick="handleClick"
          :status="status"
        />
      </view>
    </view>
  </view>
</view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtLoadMore } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtLoadMore
  },
  data() {
    return {
      status: 'more'
    }
  },
  mounted() {
  },
  methods: {
    handleClick() {
      this.status = 'loading';
      setTimeout(() => {
        this.status = 'noMore';
      }, 2000);
    }
  }
}
</script>
