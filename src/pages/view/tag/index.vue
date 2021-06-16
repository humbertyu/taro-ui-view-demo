<template>
  <view class='page'>
    <DocsHeader title='Tag 标签'></DocsHeader>

    <view class='doc-body'>
      <!--   空心标签   -->
      <view class='panel'>
        <view class='panel__title'>空心标签</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='subitem' v-for="(item, index) in hollowTagList" :key="`at-tag-${index}`">
              <AtTag
                :name="item.name"
                :active="item.active"
                :circle="index % 2 === 0"
                :onClick="handleHollowClick"
              >
                标签
              </AtTag>
            </view>
          </view>
        </view>
      </view>

      <!--   实心标签   -->
      <view class='panel'>
        <view class='panel__title'>实心标签</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='subitem' v-for="(item, index) in solidTagList" :key="`at-tag-${index}`">
              <AtTag
                type='primary'
                :name="item.name"
                :active="item.active"
                :circle="index % 2 === 0"
                :onClick="handleSolidClick"
              >
                标签
              </AtTag>
            </view>
          </view>
        </view>
      </view>

      <!--   点击事件   -->
      <view class='panel'>
        <view class='panel__title'>点击事件</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='subitem' v-for="(item, index) in tagList" :key="`at-tag-${index}`">
              <AtTag
                :name="item.name"
                type='primary'
                :active="item.active"
                :circle="index % 2 === 0"
                :onClick="onClick"
              >
                tag-{{index + 1}}
              </AtTag>
            </view>
          </view>
        </view>
      </view>

      <!--   不可点击态   -->
      <view class='panel'>
        <view class='panel__title'>不可点击态</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='subitem'>
              <AtTag type='primary' circle disabled>
                标签
              </AtTag>
            </view>
            <view class='subitem'>
              <AtTag type='primary' disabled>
                标签
              </AtTag>
            </view>
          </view>
        </view>
      </view>

      <!--   空心标签（小）   -->
      <view class='panel'>
        <view class='panel__title'>空心标签（小）</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='subitem' v-for="(item, index) in hollowTagList2" :key="`at-tag-${index}`">
              <AtTag
                size='small'
                :name="item.name"
                :active="item.active"
                :circle="index % 2 === 0"
                :onClick="handleHollowSmallClick"
              >
                标签
              </AtTag>
            </view>
          </view>
        </view>
      </view>

      <!--   实心标签（小）   -->
      <view class='panel'>
        <view class='panel__title'>实心标签（小）</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='subitem' v-for="(item, index) in solidTagList2" :key="`at-tag-${index}`">
              <AtTag
                size='small'
                type='primary'
                :name="item.name"
                :active="item.active"
                :circle="index % 2 === 0"
                :onClick="handleSolidSmallClick"
              >
                标签
              </AtTag>
            </view>
          </view>
        </view>
      </view>

      <!--   不可点击态（小）   -->
      <view class='panel'>
        <view class='panel__title'>不可点击态（小）</view>
        <view class='panel__content'>
          <view class='example-item'>
            <view class='subitem'>
              <AtTag size='small' type='primary' circle disabled>
                标签
              </AtTag>
            </view>
            <view class='subitem'>
              <AtTag size='small' type='primary' disabled>
                标签
              </AtTag>
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
import { AtTag } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

export default {
  components: {
    DocsHeader,
    AtTag
  },
  data() {
    return {
      tagList: [
        { name: 'tag-1', active: false },
        { name: 'tag-2', active: false },
        { name: 'tag-3', active: true },
        { name: 'tag-4', active: true }
      ],
      hollowTagList: [
        { name: '标签1', active: false },
        { name: '标签2', active: false },
        { name: '标签3', active: true },
        { name: '标签4', active: true }
      ],
      solidTagList: [
        { name: '标签1', active: false },
        { name: '标签2', active: false },
        { name: '标签3', active: true },
        { name: '标签4', active: true }
      ],
      hollowTagList2: [
        { name: '标签1', active: false },
        { name: '标签2', active: false },
        { name: '标签3', active: true },
        { name: '标签4', active: true }
      ],
      solidTagList2: [
        { name: '标签1', active: false },
        { name: '标签2', active: false },
        { name: '标签3', active: true },
        { name: '标签4', active: true }
      ]
    }
  },
  mounted() {
  },
  methods: {
    handleHollowClick(data) {
      const findIndex = this.hollowTagList.findIndex(item => item.name === data.name);
      this.hollowTagList[findIndex].active = !this.hollowTagList[findIndex].active
    },
    handleSolidClick(data) {
      const findIndex = this.solidTagList.findIndex(item => item.name === data.name)
      this.solidTagList[findIndex].active = !this.solidTagList[findIndex].active
    },
    onClick(data) {
      const findIndex = this.tagList.findIndex(item => item.name === data.name)
      const active = !this.tagList[findIndex].active
      const content = `您点击的 tag 标签名是：${data.name}，点击前是否选中：${data.active}，点击后：${active}`

      this.tagList[findIndex].active = active

      if (Taro.getEnv() === Taro.ENV_TYPE.WEB) {
        alert(content)
      } else {
        Taro.showModal({ content, showCancel: false })
      }
    },
    handleHollowSmallClick(data) {
      const findIndex = this.hollowTagList2.findIndex(item => item.name === data.name)

      this.hollowTagList2[findIndex].active = !this.hollowTagList2[findIndex].active
    },
    handleSolidSmallClick(data) {
      const findIndex = this.solidTagList2.findIndex(item => item.name === data.name)

      this.solidTagList2[findIndex].active = !this.solidTagList2[findIndex].active
    }
  }
}
</script>
