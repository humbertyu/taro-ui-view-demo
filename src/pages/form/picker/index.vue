<template>
  <view class='page picker__page'>
    <DocsHeader title='Picker 选择器'></DocsHeader>

    <view class='doc-body'>
      <!--   普通选择器   -->
      <view class='panel'>
        <view class='panel__title'>普通选择器</view>
        <view class='panel__content'>
          <view class='example-item'>
            <picker
              mode='selector'
              :range="selector"
              :value="selectorValue"
              @change="handleChange"
            >
              <view class='demo-list-item'>
                <view class='demo-list-item__label'>国家地区</view>
                <view class='demo-list-item__value'>
                  {{ selector[selectorValue] }}
                </view>
              </view>
            </picker>
          </view>
        </view>
      </view>

      <!--   多列选择器   -->
      <view v-if="!isAlipay" class='panel'>
        <view class='panel__title'>多列选择器</view>
        <view class='panel__content'>
          <view class='example-item'>
            <picker
              mode='multiSelector'
              :range="multiSelector"
              :value="mulitSelectorValues"
              @change="handleMultiChange"
            >
              <view class='demo-list-item'>
                <view class='demo-list-item__label'>请选择早餐</view>
                <view class='demo-list-item__value'>{{`${
                  multiSelector[0][mulitSelectorValues[0]]
                  } & ${multiSelector[1][mulitSelectorValues[1]]}`}}</view>
              </view>
            </picker>
          </view>
        </view>
      </view>

      <!--   时间选择器   -->
      <view class='panel'>
        <view class='panel__title'>时间选择器</view>
        <view class='panel__content'>
          <view class='example-item'>
            <picker
              mode='time'
              :value="timeSel"
              @change="handleTimeChange"
            >
              <view class='demo-list-item'>
                <view class='demo-list-item__label'>请选择时间</view>
                <view class='demo-list-item__value'>{{ timeSel }}</view>
              </view>
            </picker>
          </view>
        </view>
      </view>

      <!--   日期选择器   -->
      <view class='panel'>
        <view class='panel__title'>日期选择器</view>
        <view class='panel__content'>
          <view class='example-item'>
            <picker
              mode='date'
              :value="dateSel"
              @change="handleDateChange"
            >
              <view class='demo-list-item'>
                <view class='demo-list-item__label'>请选择日期</view>
                <view class='demo-list-item__value'>{{ dateSel }}</view>
              </view>
            </picker>
          </view>
        </view>
      </view>

    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import Taro from '@tarojs/taro'

export default {
  components: {
    DocsHeader
  },
  data() {
    return {
      selector: ['中国', '美国', '巴西', '日本'],
      multiSelector: [
        ['饭', '粥', '粉'],
        ['猪肉', '牛肉']
      ],
      selectorValue: 0,
      mulitSelectorValues: [0, 1],
      timeSel: '06:18',
      dateSel: '2018-06-18',
      isAlipay: false
    }
  },
  computed: {
  },
  mounted() {
    this.isAlipay = Taro.getEnv() == Taro.ENV_TYPE.ALIPAY;
  },
  methods: {
    handleChange(e) {
      this.selectorValue = e.detail.value;
    },
    handleMultiChange(e) {
      this.mulitSelectorValues = e.detail.value;
    },
    handleTimeChange(e) {
      console.log("time", e)
      this.timeSel = e.detail.value;
    },
    handleDateChange(e) {
      console.log("date", e);
      this.dateSel = e.detail.value;
    }
  }
}
</script>
