<template>
  <view class='page swipe-action-page'>
    <DocsHeader title='SwipeAction 滑动操作' />

    <view class='doc-body'>
      <!--   无 Title   -->
      <view class='panel'>
        <view class='panel__title'>一般用法</view>
        <view class='panel__content no-padding'>
          <view class='example-item example-item--border'>
            <AtSwipeAction :onClick="handleClick" :options="options">
              <view class='normal'>AtSwipeAction 一般使用场景</view>
            </AtSwipeAction>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>禁止滑动</view>
        <view class='panel__content no-padding'>
          <view class='example-item example-item--border'>
            <AtSwipeAction disabled :options="options">
              <view class='normal'>禁止滑动展示</view>
            </AtSwipeAction>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>使用变量控制开关</view>
        <view class='panel__controller' style='margin-bottom: 10px'>
          <AtButton size='small' :onClick="handleStatusClick">
            当前状态: {{isOpened2 ? '开' : '关'}}{{' '}}
          </AtButton>
        </view>

        <view class='panel__content no-padding'>
          <view class='example-item example-item--border'>
            <AtSwipeAction
              :options="options"
              :disabled="!isOpened2"
              :isOpened="isOpened2"
              :onClosed="handleStatusClosed"
              :onOpened="handleStatusOpened"
            >
              <view class='normal'>使用变量控制开关</view>
            </AtSwipeAction>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>自动关闭</view>
        <view class='panel__content no-padding'>
          <view class='example-item example-item--border'>
            <AtSwipeAction
              :onClick="handleClick"
              autoClose
              :options="options"
            >
              <view class='normal'>点击按钮自动关闭</view>
            </AtSwipeAction>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>传递点击事件</view>
        <view class='panel__content no-padding'>
          <view class='example-item example-item--border'>
            <AtSwipeAction :onClick="handleClick" :options="options">
              <view class='normal'>点击事件触发</view>
            </AtSwipeAction>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>开启和关闭事件</view>
        <view class='panel__content no-padding'>
          <view class='example-item example-item--border'>
            <AtSwipeAction
              :options="options"
              :onClick="handleClick"
              :on-opened="handleOpened"
              :on-closed="handleClosed"
            >
              <view class='normal'>开启和关闭时触发事件</view>
            </AtSwipeAction>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>与List组件使用</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtList>
              <AtSwipeAction :options="options">
                <AtListItem title='Item1' />
              </AtSwipeAction>
              <AtSwipeAction :options="options">
                <AtListItem title='Item2' />
              </AtSwipeAction>
              <AtSwipeAction
                :options="[
                {
                text: '警告',
                style: {
                  backgroundColor: '#FFC82C'
                  }
                }
              ]"
              >
              <AtListItem title='Item3123123123123' />
              </AtSwipeAction>
            </AtList>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>控制只显示单个</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtList>
              <AtSwipeAction
                v-for="item in list"
                :key="item.title"
                :options="item.options"
                :isOpened="item.isOpened"
                :on-click="handleClicked"
                :on-opened="handleSingle"
              >
                <AtListItem :title="item.title" />
              </AtSwipeAction>
            </AtList>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtSwipeAction, AtButton, AtList, AtListItem } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

const OPTIONS = [
  {
    text: '删除',
    style: {
      color: '#333',
      backgroundColor: '#F7F7F7'
    }
  },
  {
    text: '确认',
    style: {
      backgroundColor: '#E93B3D'
    }
  }
];
export default {
  components: {
    DocsHeader,
    AtSwipeAction,
    AtButton,
    AtList,
    AtListItem
  },
  data() {
    return {
      isOpened2: false,
      list: [
        {
          title: 'item1',
          isOpened: false,
          options: OPTIONS
        },
        {
          title: 'item2',
          isOpened: false,
          options: OPTIONS
        },
        {
          title: 'item3',
          isOpened: false,
          options: OPTIONS
        },
        {
          title: 'item4',
          isOpened: false,
          options: OPTIONS
        },
        {
          title: 'item5',
          isOpened: false,
          options: OPTIONS
        },
        {
          title: 'item6',
          isOpened: false,
          options: OPTIONS
        }
      ],
      options: [
        {
          text: '删除',
          style: {
            color: '#333',
            backgroundColor: '#F7F7F7'
          }
        },
        {
          text: '确认',
          style: {
            backgroundColor: '#E93B3D'
          }
        }
      ]
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    showToast(name) {
      Taro.showToast({
        icon: 'none',
        title: name
      })
    },
    handleClick(item, key) {
      this.showToast(`点击了${item.text}按钮，Key: ${key}`);
    },
    handleClicked(index) {
      const list = this.list.filter((_item, key) => key !== index)
      this.list = list;
    },
    handleStatusClick() {
      this.isOpened2 = !this.isOpened2
    },
    handleStatusOpened() {
      this.isOpened2 = true;
    },
    handleStatusClosed() {
      this.isOpened2 = false;
    },
    handleSingle() {
      const list = this.list.map((item, key) => {
        item.isOpened = key === index
        return item
      })
      this.list = list;
    },
    handleOpened() {
      this.showToast('Handle Opened')
    },
    handleClosed() {
      this.showToast('Handle Closed')
    }
  }
}
</script>
