<template>
  <view class='page'>
    <DocsHeader title='ActionSheet 动作面板' />

    <view class='doc-body'>
      <!--   无 Title   -->
      <view class='panel'>
        <view class='panel__title'>无标题</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton :onClick="this.handleClick.bind(this, 1)">
              打开 ActionSheet
            </AtButton>
          </view>
        </view>
      </view>

      <!--   含标题   -->
      <view class='panel'>
        <view class='panel__title'>含标题</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton :onClick="this.handleClick.bind(this, 2)">
              打开 ActionSheet
            </AtButton>
          </view>
        </view>
      </view>

      <!--   自定义选项   -->
      <view class='panel'>
        <view class='panel__title'>自定义选项</view>
        <view class='panel__content'>
          <view class='example-item'>
            <AtButton :onClick="this.handleClick.bind(this, 3)">
              打开 ActionSheet
            </AtButton>
          </view>
        </view>
      </view>
    </view>

    <AtActionSheet
      cancelText='取消'
      :isOpened="isOpened1"
      :onClose="this.handleClose.bind(this, 1)"
    >
      <AtActionSheetItem
        :onClick="this.showToast.bind(this, '点击了按钮一')"
      >
      按钮一
      </AtActionSheetItem>
      <AtActionSheetItem
        :onClick="this.showToast.bind(this, '点击了按钮二')"
      >
      按钮二
      </AtActionSheetItem>
    </AtActionSheet>

    <AtActionSheet
      cancelText='取消'
      :isOpened="isOpened2"
      :onClose="this.handleClose.bind(this, 2)"
      title='清除位置信息后， 别人将不能查看到你'
    >
      <AtActionSheetItem
        :onClick="this.showToast.bind(this, '点击了按钮一')"
      >
      按钮一
      </AtActionSheetItem>
      <AtActionSheetItem
        :onClick="this.showToast.bind(this, '点击了按钮二')"
      >
      按钮二
      </AtActionSheetItem>
    </AtActionSheet>

    <AtActionSheet
      cancelText='取消'
      :isOpened="isOpened3"
      :onCancel="handleCancel"
      :onClose="this.handleClose.bind(this, 3)"
      title='清除位置信息后， 别人将不能查看到你'
    >
      <AtActionSheetItem
        :onClick="this.showToast.bind(this, '点击了按钮一')"
      >
      按钮一
      </AtActionSheetItem>
      <AtActionSheetItem
        :onClick="this.showToast.bind(this, '点击了按钮二')"
      >
      按钮二
      </AtActionSheetItem>
      <AtActionSheetItem
        :onClick="this.showToast.bind(this, '成功清除位置')"
      >
      <text class='danger'>清除位置信息并退出</text>
      </AtActionSheetItem>
    </AtActionSheet>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtActionSheet, AtActionSheetItem, AtButton } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

export default {
  components: {
    DocsHeader,
    AtActionSheet,
    AtActionSheetItem,
    AtButton
  },
  data() {
    return {
      isOpened1: false,
      isOpened2: false,
      isOpened3: false
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    handleClick(type) {
      this[`isOpened${type}`] = true;
    },
    handleClose(name) {
      this[`isOpened${name}`] = false;
      Taro.showToast({
        title: `第 ${name} 个Action Sheet已经关闭`,
        icon: 'none'
      });
    },
    showToast(name) {
      Taro.showToast({
        icon: 'none',
        title: name
      })
    },
    handleCancel() {
      this.showToast('点击了取消按钮');
    }
  }
}
</script>
