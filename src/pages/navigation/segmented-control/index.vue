<template>
  <view class='page'>
    <DocsHeader title='Segmented Control 分段器'></DocsHeader>

    <view class='doc-body'>
      <!--   基础用法   -->
      <view class='panel'>
        <view class='panel__title'>基础用法</view>
        <view class='panel__content'>
          <view>
            <AtSegmentedControl
              :onClick="this.handleClick.bind(this, 1)"
              :current="current1"
              :values="tabList2"
            />
            <view class='tab-content'>标签 {{current1 + 1}} 的内容</view>
          </view>
        </view>
      </view>

      <!--   自定义   -->
      <view class='panel'>
        <view class='panel__title'>自定义颜色、字体大小</view>
        <view class='panel__content'>
          <view>
            <AtSegmentedControl
              :onClick="this.handleClick.bind(this, 2)"
              selectedColor='#FF4949'
              :fontSize="30"
              :current="current2"
              :values="tabList2"
            />
            <view class='tab-content'>标签 {{current2 + 1}} 的内容</view>
          </view>
        </view>
      </view>

      <!--   禁用   -->
      <view class='panel'>
        <view class='panel__title'>禁用</view>
        <view class='panel__content'>
          <AtSegmentedControl disabled :values="tabList1" />
        </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtSegmentedControl } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtSegmentedControl
  },
  data() {
    return {
      current1: 0,
      current2: 0,
      tabList1: ['标签页1', '标签页2'],
      tabList2: ['标签页1', '标签页2', '标签页3']
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    handleClick(num, value) {
      this[`current${num}`] = value;
    }
  }
}
</script>
