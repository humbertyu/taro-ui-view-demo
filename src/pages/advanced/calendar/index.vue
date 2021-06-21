<template>
  <view class='page calendar-page'>
    <DocsHeader title='Calendar 日历' />

    <view class='doc-body'>
      <view class='panel'>
        <view class='panel__title'>一般案例</view>
        <view class='panel__content'>
          <AtCalendar onMonthChange={this.handleMonthChange} />
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>跳转到指定日期</view>
        <view class='panel__content'>
          <AtCalendar :currentDate="now" />
          <view class='body_controllers'>
            <AtButton
              size='small'
              :onClick="this.handleClick.bind(this, 'now', '2018/01/01')"
            >
            跳转到 2018/01/01
            </AtButton>
            <AtButton
              size='small'
              :onClick="this.handleClick.bind(this, 'now', '2018/06/18')"
            >
            跳转到 2018/6/18
            </AtButton>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>指定最小日期和最大日期</view>
        <view class='panel__content'>
          <AtCalendar :minDate="minDate" :maxDate="maxDate" />
          <view class='body_controllers'>
            <AtButton
              size='small'
              :onClick="this.handleClick.bind(this, 'minDate', '2018/01/01')"
            >
            设置最小值 2018/1/1
            </AtButton>
            <AtButton
              size='small'
              :onClick="this.handleClick.bind(this, 'maxDate', '2019/12/31')"
            >
            设置最大值 2019/12/31
            </AtButton>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>标记时间</view>
        <view class='panel__content'>
          <AtCalendar :marks="mark" />
          <view class='body_controllers'>
            <AtButton
              size='small'
              class='button'
              :onClick="this.handleClick.bind(this, 'mark', [
                {
                value: Date.now()
                }
                ])"
            >
            标记当前时间
            </AtButton>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>禁止滑动</view>
        <view class='panel__content'>
          <AtCalendar :isSwiper="false" />
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>垂直滑动</view>
        <view class='panel__content'>
          <AtCalendar isVertical :onSelectDate="handleDateChange" />
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>范围选择</view>
        <view class='panel__content'>
          <AtCalendar
            :onSelectDate="handleDateChange"
            isMultiSelect
            :currentDate="multiCurrentDate"
          />
          <view class='body_controllers'>
            <AtButton
              size='small'
              class='button'
              :onClick="this.handleClick.bind(this, 'multiCurentDate', {
                start: '2018/10/28',
                end: '2018/11/11'
                })"
            >
            设置选择区间为 2018/10/28 - 2018/11/11
            </AtButton>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>有效时间组</view>
        <view class='panel__content'>
          <AtCalendar :validDates="validDates" />
        </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtCalendar, AtButton } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

export default {
  components: {
    DocsHeader,
    AtCalendar,
    AtButton
  },
  data() {
    return {
      now: Date.now(),
      minDate: '2018/06/11',
      maxDate: '2020/12/12',
      multiCurrentDate: {
        start: Date.now()
      },
      mark: [
        {
          value: '2018/11/11'
        }
      ],
      validDates: [
        {
          value: '2019/04/17'
        },
        {
          value: '2019/04/21'
        },
        {
          value: '2019/05/04'
        },
        {
          value: '2019/05/28'
        }
      ]
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    handleClick(key, value) {
      this[key] = value;
    },
    handleDateChange(arg) {
      Taro.showToast({
        title: `handleDateChange: ${JSON.stringify(arg)}`,
        icon: 'none'
      })
    },
    handleMonthChange(arg) {
      Taro.showToast({
        title: `handleMonthChange: ${JSON.stringify(arg)}`,
        icon: 'none'
      })
    }
  }
}
</script>
