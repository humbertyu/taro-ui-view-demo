<template>
  <view class='page'>
    <DocsHeader title='Button 按钮'></DocsHeader>
    <view class='doc-body'>
      <!--   主操作   -->
      <view class='panel'>
        <view class='panel__title'>主操作</view>
        <view class='panel__content'>
          <view class='btn-item'>
            <AtButton
              type='primary'
              :on-click="onButtonClick"
            >
              主操作按钮
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton
              type='primary'
              loading
              :on-click="onButtonClick"
            >
              Loading
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton type='primary' disabled>
              不可操作
            </AtButton>
          </view>
        </view>
      </view>

      <!--   次要操作   -->
      <view class='panel'>
        <view class='panel__title'>次要操作</view>
        <view class='panel__content'>
          <view class='btn-item'>
            <AtButton type='secondary'>次操作按钮</AtButton>
          </view>
          <view class='btn-item'>
            <AtButton type='secondary' loading>
              Loading
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton type='secondary' disabled>
              不可操作
            </AtButton>
          </view>
        </view>
      </view>

      <!--   次次要操作   -->
      <view class='panel'>
        <view class='panel__title'>次次要操作</view>
        <view class='panel__content'>
          <view class='btn-item'>
            <AtButton>次次要操作按钮</AtButton>
          </view>
          <view class='btn-item'>
            <AtButton loading>Loading</AtButton>
          </view>
          <view class='btn-item'>
            <AtButton disabled>不可操作</AtButton>
          </view>
        </view>
      </view>

      <!--   通栏   -->
      <view class='panel'>
        <view class='panel__title'>通栏按钮</view>
        <view class='panel__content' style='padding:0'>
          <view class='btn-item'>
            <AtButton type='primary' full>
              主操作按钮
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton type='secondary' full>
              次操作按钮
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton full>次次要操作按钮</AtButton>
          </view>
          <view class='btn-item'>
            <AtButton disabled full>
              不可操作
            </AtButton>
          </view>
        </view>
      </view>

      <!--   小按钮   -->
      <view class='panel'>
        <view class='panel__title'>小按钮</view>
        <view class='panel__content'>
          <view class='btn-item'>
            <view class='subitem'>
              <AtButton type='primary' size='small'>
                按钮
              </AtButton>
            </view>
            <view class='subitem'>
              <AtButton type='secondary' size='small'>
                按钮
              </AtButton>
            </view>
            <view class='subitem'>
              <AtButton size='small'>按钮</AtButton>
            </view>
          </view>
          <view class='btn-item'>
            <view class='subitem'>
              <AtButton type='primary' size='small' loading></AtButton>
            </view>
            <view class='subitem'>
              <AtButton type='secondary' size='small' loading></AtButton>
            </view>
            <view class='subitem'>
              <AtButton size='small' loading></AtButton>
            </view>
          </view>
          <view class='btn-item'>
            <view class='subitem'>
              <AtButton type='primary' size='small' disabled>
                按钮
              </AtButton>
            </view>
            <view class='subitem'>
              <AtButton type='secondary' size='small' disabled>
                按钮
              </AtButton>
            </view>
            <view class='subitem'>
              <AtButton size='small' disabled>
                按钮
              </AtButton>
            </view>
          </view>
        </view>
      </view>

      <!--   圆角按钮   -->
      <view class='panel'>
        <view class='panel__title'>圆角按钮</view>
        <view class='panel__content'>
          <view class='btn-item'>
            <view class='subitem'>
              <AtButton type='primary' size='small' circle>
                按钮
              </AtButton>
            </view>
            <view class='subitem'>
              <AtButton type='secondary' size='small' circle>
                按钮
              </AtButton>
            </view>
            <view class='subitem'>
              <AtButton size='small' circle>
                按钮
              </AtButton>
            </view>
          </view>
          <view class='btn-item'>
            <view class='subitem'>
              <AtButton
                type='primary'
                size='small'
                loading
                circle
              ></AtButton>
            </view>
            <view class='subitem'>
              <AtButton
                type='secondary'
                size='small'
                loading
                circle
              ></AtButton>
            </view>
            <view class='subitem'>
              <AtButton size='small' loading circle></AtButton>
            </view>
          </view>
          <view class='btn-item'>
            <view class='subitem'>
              <AtButton type='primary' size='small' disabled circle>
                按钮
              </AtButton>
            </view>
            <view class='subitem'>
              <AtButton type='secondary' size='small' disabled circle>
                按钮
              </AtButton>
            </view>
            <view class='subitem'>
              <AtButton size='small' disabled circle>
                按钮
              </AtButton>
            </view>
          </view>
        </view>
      </view>

      <!--   浮动按钮   -->
      <view class='panel' v-if="!isALIPAY">
        <view class='panel__title'>浮动按钮</view>
        <view class='panel__content'>
          <view class='at-article__p'>右侧是浮动操作按钮👉</view>
          <view class='btn-demo-fab'>
            <AtFab :on-click="onButtonClick">
              <text class='at-fab__icon at-icon at-icon-menu'></text>
            </AtFab>
          </view>
        </view>
      </view>

      <!--   微信小程序 button 属性（仅部分支持）   -->
      <view class='panel' v-if="isWEAPP">
        <view class='panel__title'>微信小程序 button 属性</view>
        <view class='panel__content'>
          <view class='btn-item'>
            <AtButton openType='share' type='primary'>
              分享
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton
              openType='getUserInfo'
              :on-get-user-info="onGetUserInfo"
              type='primary'
            >
              登录授权
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton
              openType='contact'
              :on-contact="onContact"
              type='secondary'
            >
              联系 Taro UI 客服
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtButton
              openType='openSetting'
              :on-open-setting="onOpenSetting"
              type='secondary'
            >
              打开设置
            </AtButton>
          </view>
          <view class='btn-item'>
            <AtForm
              reportSubmit
            >
              <view class='btn-item'>
                <AtButton type='primary' formType='submit' :onClick="onSubmit">
                  form submit
                </AtButton>
              </view>
              <view class='btn-item'>
                <AtButton type='secondary' formType='reset' :onClick="onReset">
                  form reset
                </AtButton>
              </view>
            </AtForm>
          </view>
        </view>
      </view>

    </view>
  </view>
</template>
<script>
import Taro from '@tarojs/taro'
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtButton, AtFab, AtForm} from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtButton,
    AtFab,
    AtForm
  },
  data() {
    return {
      isALIPAY: "",

      isWEAPP: ""
    }
  },
  mounted() {

    this.isALIPAY = Taro.getEnv() == Taro.ENV_TYPE.ALIPAY;
    this.isWEAPP = Taro.getEnv() == Taro.ENV_TYPE.WEAPP;
  },
  methods: {
    onButtonClick() {
      const content = [...arguments].find(item => typeof item === 'string')
      const ENV = Taro.getEnv()
      if (ENV === 'WEAPP') {
      Taro.showModal({
        content: content || '您点击了按钮！',
        showCancel: false
        })
      }
      if (ENV === 'WEB') {
        alert(content || '您点击了按钮！')
      }
    },
    onGetUserInfo(event) {
      Taro.showModal({
        content: `getUserInfo event detail: ${JSON.stringify(event.detail)}`
      })
    },
    onContact(event) {
      Taro.showToast({
        title: `呼起客服回调: ${event.detail}`
      })
    },
    onOpenSetting(event) {
      Taro.showToast({
        title: `onOpenSetting: ${event.detail}`
      })
    },
    onSubmit(event) {
      Taro.showModal({
        content: `submit event detail: ${JSON.stringify(event.detail)}`,
        showCancel: false
      })
    },
    onReset(event) {
      Taro.showModal({
        content: `reset event detail: ${JSON.stringify(
          event.detail || '无数据'
        )}`,
        showCancel: false
      })
    }
  }
}
</script>
