<template>
  <view class='page'>
    <DocsHeader title='ICON 图标'></DocsHeader>
    <view class='doc-body'>
      <view class='panel'>
        <view class='panel__title'>主要</view>
        <view class='panel__content'>
          <view class='icon-list'>
            <view class='icon-list__item' v-for="(icon, index) in icons.main" :key="'at-icon-' + index">
              <view class='icon-list__icon'>
                <AtIcon
                  :value="icon"
                  :color="iconColor"
                  :size="iconSize"
                ></AtIcon>
              </view>
              <view class='icon-list__name'>{{ icon }}</view>
            </view>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>文本</view>
        <view class='panel__content'>
          <view class='icon-list'>
            <view class='icon-list__item' v-for="(icon, index) in icons.text" :key="'at-icon-' + index">
              <view class='icon-list__icon'>
                <AtIcon
                  :value="icon"
                  :color="iconColor"
                  :size="iconSize"
                ></AtIcon>
              </view>
              <view class='icon-list__name'>{{ icon }}</view>
            </view>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>箭头</view>
        <view class='panel__content'>
          <view class='icon-list'>
            <view class='icon-list__item' v-for="(icon, index) in icons.arrow" :key="'at-icon-' + index">
              <view class='icon-list__icon'>
                <AtIcon
                  :value="icon"
                  :color="iconColor"
                  :size="iconSize"
                ></AtIcon>
              </view>
              <view class='icon-list__name'>{{ icon }}</view>
            </view>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>媒体控制</view>
        <view class='panel__content'>
          <view class='icon-list'>
            <view class='icon-list__item' v-for="(icon, index) in icons.media" :key="'at-icon-' + index">
              <view class='icon-list__icon'>
                <AtIcon
                  :value="icon"
                  :color="iconColor"
                  :size="iconSize"
                ></AtIcon>
              </view>
              <view class='icon-list__name'>{{ icon }}</view>
            </view>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>多媒体</view>
        <view class='panel__content'>
          <view class='icon-list'>
            <view class='icon-list__item' v-for="(icon, index) in icons.photo" :key="'at-icon-' + index">
              <view class='icon-list__icon'>
                <AtIcon
                  :value="icon"
                  :color="iconColor"
                  :size="iconSize"
                ></AtIcon>
              </view>
              <view class='icon-list__name'>{{ icon }}</view>
            </view>
          </view>
        </view>
      </view>

      <view class='panel'>
        <view class='panel__title'>Logo</view>
        <view class='panel__content'>
          <view class='icon-list'>
            <view class='icon-list__item' v-for="(icon, index) in icons.logo" :key="'at-icon-' + index">
              <view class='icon-list__icon'>
                <AtIcon
                  :value="icon"
                  :color="iconColor"
                  :size="iconSize"
                ></AtIcon>
              </view>
              <view class='icon-list__name'>{{ icon }}</view>
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
import "taro-ui-vue/dist/style/components/icon.scss";
import icons from "./icons";
import { AtIcon } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtIcon
  },
  data() {
    return {
      icons: icons,
      iconColor: '#999',
      iconSize: 30
    }
  },
  mounted() {
  },
  methods: {}
}
</script>
