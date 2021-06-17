<template>
  <view class='page'>
    <DocsHeader title='Steps 步骤条'></DocsHeader>

    <view class='doc-body'>
      <!--   基础用法   -->
      <view class='panel'>
        <view class='panel__title'>基础用法</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtSteps
              :items="items1"
              :current="current1"
              :onChange="this.onChange.bind(this, 'current1')"
            />
            <AtSteps
              :items="items2"
              :current="current2"
              :onChange="this.onChange.bind(this, 'current2')"
            />
          </view>
        </view>
      </view>

      <!--   带附加信息   -->
      <view class='panel'>
        <view class='panel__title'>带附加信息</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtSteps
              :items="items3"
              :current="current3"
              :onChange="this.onChange.bind(this, 'current3')"
            />
          </view>
        </view>
      </view>

      <!--   自定义图标   -->
      <view class='panel'>
        <view class='panel__title'>自定义图标</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtSteps
              :items="items4"
              :current="current4"
              :onChange="this.onChange.bind(this, 'current4')"
            />
          </view>
        </view>
      </view>

      <!--   状态步骤条   -->
      <view class='panel'>
        <view class='panel__title'>状态步骤条</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtSteps
              :items="items5"
              :current="current5"
              :onChange="this.onChange.bind(this, 'current5')"
            />
          </view>
        </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtSteps } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtSteps
  },
  data() {
    return {
      items1: [{ title: '步骤一' }, { title: '步骤二' }],
      items2: [
        { title: '步骤一' },
        { title: '步骤二' },
        { title: '步骤三' }
      ],
      items3: [
        { title: '步骤一', desc: '这里是额外的信息，最多两行' },
        { title: '步骤二', desc: '这里是额外的信息，最多两行' },
        { title: '步骤三', desc: '这里是额外的信息，最多两行' }
      ],
      items4: [
        {
          title: '步骤一',
          desc: '这里是额外的信息，最多两行',
          icon: {
            value: 'sound',
            activeColor: '#fff',
            inactiveColor: '#78A4FA',
            size: '14'
          }
        },
        {
          title: '步骤二',
          desc: '这里是额外的信息，最多两行',
          icon: {
            value: 'shopping-cart',
            activeColor: '#fff',
            inactiveColor: '#78A4FA',
            size: '14'
          }
        },
        {
          title: '步骤三',
          desc: '这里是额外的信息，最多两行',
          icon: {
            value: 'camera',
            activeColor: '#fff',
            inactiveColor: '#78A4FA',
            size: '14'
          }
        }
      ],
      items5: [
        {
          title: '步骤一',
          desc: '这里是额外的信息，最多两行',
          status: 'success'
        },
        {
          title: '步骤二',
          desc: '这里是额外的信息，最多两行'
        },
        {
          title: '步骤三',
          desc: '这里是额外的信息，最多两行',
          status: 'error'
        }
      ],
      current1: 0,
      current2: 0,
      current3: 0,
      current4: 0,
      current5: 1
    }
  },
  mounted() {
  },
  methods: {
    onChange(stateName, current) {
      this[stateName] = current;
    }
  }
}
</script>
