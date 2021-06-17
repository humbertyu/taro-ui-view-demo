<template>
  <view class='page'>
    <DocsHeader title='Switch 开关'></DocsHeader>

    <view class='doc-body'>
      <!--  基础用法  -->
      <view class='panel'>
        <view class='panel__title'>基础用法</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtForm>
              <AtSwitch
                title='开启中'
                :checked="switchValue"
                :onChange="handleChange"
              />
              <AtSwitch title='已关闭' :border="false" />
            </AtForm>
          </view>
        </view>
      </view>

      <!--  禁用状态  -->
      <view class='panel'>
        <view class='panel__title'>禁用状态</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtForm>
              <AtSwitch title='不可点击' checked disabled />
              <AtSwitch title='不可点击' :border="false" disabled />
            </AtForm>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtSwitch, AtForm } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtSwitch,
    AtForm
  },
  data() {
    return {
      switchValue: true
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    handleChange(value) {
      this.switchValue = value;
    }
  }
}
</script>
