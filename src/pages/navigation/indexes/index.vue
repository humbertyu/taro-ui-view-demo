<template>
  <view
    class="page"
    style="height: 100vh;"
  >
    <!-- 基础用法 -->
    <view style="height: 100%;">
      <AtIndexes
        :list="mockData"
        topKey="Top"
        :onClick="onClick"
        :onScrollIntoView="handleScroll"
      >
        <view class="custom-area">
          用户自定义内容
          <AtSearchBar
            :value="value"
            :onChange="handleChange"
            placeholder="跳转到指定Key"
            :onActionClick="handleActionClick"
          />
        </view>
      </AtIndexes>
    </view>
  </view>
</template>
<script>
import './index.scss'
import { AtIndexes, AtSearchBar } from 'taro-ui-vue'
import Taro from '@tarojs/taro'
import city from "../../mock-data/mock-data";

export default {
  components: {
    AtIndexes,
    AtSearchBar
  },
  data() {
    return {
      mockData: city,
      value: '',
      scrollToView: null
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {

    scrollIntoView(key) {
      Taro.showToast({
        title: `scrollIntoView: ${key}`,
        icon: 'none',
      })
    },
    onClick(item) {
      Taro.showToast({
        title: `onClick: ${JSON.stringify(item.name)}:  ${JSON.stringify(item.key)}`,
        icon: 'none',
      })
    },
    handleActionClick() {
      if (!this.value) {
        return
      }
      this.scrollToView && this.scrollToView(this.value.toUpperCase())
      this.value = ''
    },
    handleChange(value) {
      this.value = value
    },
    handleScroll(fn) {
      this.scrollToView = fn
    }
  }
}
</script>
