<template>
  <view class='page'>
    <DocsHeader title='Input 输入框'></DocsHeader>

    <view class='doc-body'>
      <!--   基础用法   -->
      <view class='panel'>
        <view class='panel__title'>基础用法</view>
        <view class='panel__content no-padding'>
          <view class='component-item'>
            <AtForm>
              <AtInput
                name='value1'
                title='标准五个字'
                type='text'
                placeholder='标准五个字'
                :value="value1"
                :onChange="this.handleInput.bind(this, 'value1')"
              />
              <AtInput
                name='value2'
                title='标题实在特别长就换行'
                placeholder='其他列保持正常间距'
                :value="value2"
                :onChange="this.handleInput.bind(this, 'value2')"
              />
              <AtInput
                name='value3'
                :border="false"
                placeholder='无标题'
                :value="value3"
                :onChange="this.handleInput.bind(this, 'value3')"
              />
            </AtForm>
          </view>
        </view>
      </view>

      <!--   输入框类型   -->
      <view class='panel'>
        <view class='panel__title'>输入框类型</view>
        <view class='panel__content no-padding'>
          <view class='component-item'>
            <AtForm>
              <AtInput
                name='value4'
                title='文本'
                type='text'
                placeholder='单行文本'
                :value="value4"
                :onChange="this.handleInput.bind(this, 'value4')"
              />
              <AtInput
                name='value5'
                title='数字'
                type='number'
                placeholder='请输入数字'
                :value="value5"
                :onChange="this.handleInput.bind(this, 'value5')"
              />
              <AtInput
                name='value6'
                title='密码'
                type='password'
                placeholder='密码不能少于10位数'
                :value="value6"
                :onChange="this.handleInput.bind(this, 'value6')"
              />
              <AtInput
                name='value7'
                title='身份证'
                type='idcard'
                placeholder='身份证号码'
                :value="value7"
                :onChange="this.handleInput.bind(this, 'value7')"
              />
              <AtInput
                name='value8'
                title='小数'
                type='digit'
                placeholder='请输入小数'
                :value="value8"
                :onChange="this.handleInput.bind(this, 'value8')"
              />
              <AtInput
                name='value9'
                :border='false'
                title='手机号码'
                type='phone'
                placeholder='手机号码'
                :value="value9"
                :onChange="this.handleInput.bind(this, 'value9')"
              />
            </AtForm>
          </view>
        </view>
      </view>

      <!--   状态   -->
      <view class='panel'>
        <view class='panel__title'>状态</view>
        <view class='panel__content no-padding'>
          <view class='component-item'>
            <AtForm>
              <AtInput
                name='value10'
                disabled
                title='禁用'
                type='text'
                placeholder='禁止输入'
                :value="value10"
                :onChange="this.handleInput.bind(this, 'value10')"
              />
              <AtInput
                name='value11'
                error
                title='出现错误'
                type='text'
                placeholder='点击按钮触发回调'
                :value="value11"
                :onChange="this.handleInput.bind(this, 'value11')"
                :onErrorClick="this.onClickErrorIcon.bind(this)"
              />
              <AtInput
                name='value12'
                :editable='false'
                title='不可编辑'
                type='text'
                placeholder='不可编辑'
                value='不可编辑的内容'
              />
              <AtInput
                name='value13'
                :border='false'
                clear
                title='清除按钮'
                type='text'
                placeholder='点击清除按钮清空内容'
                :value="value13"
                :onChange="this.handleInput.bind(this, 'value13')"
              />
              <AtInput
                name='value16'
                :border='false'
                required
                title='必填项'
                type='text'
                placeholder='必填项'
                :value="value16"
                :onChange="this.handleInput.bind(this, 'value16')"
              />
              <AtInput
                name='value17'
                :border='false'
                title='监听事件'
                type='text'
                placeholder='监听键盘高度事件'
                :value="value17"
                :onChange="this.handleInput.bind(this, 'value17')"
                :onKeyboardHeightChange="handleKeyboardHeightChange"
              />
            </AtForm>
          </view>
        </view>
      </view>

      <!--   自定义右边栏   -->
      <view class='panel'>
        <view class='panel__title'>自定义右边栏</view>
        <view class='panel__content no-padding'>
          <view class='component-item'>
            <AtForm>
              <AtInput
                name='value14'
                title='验证码'
                type='text'
                :maxLength='4'
                clear
                placeholder='验证码'
                :value="value14"
                :onChange="this.handleInput.bind(this, 'value14')"
              >
                <image :src="verificationCode" />
              </AtInput>
              <AtInput
                name='value15'
                :border='false'
                type='phone'
                clear
                placeholder='请输入手机号码'
                :value="value15"
                :onChange="this.handleInput.bind(this, 'value15')"
              >
              <view
                :style="{
                  color: this.disabled ? '#FF4949' : '',
                  fontSize: '12px',
                  width: '90px'
                }"
                @tap="sendCode"
              >
              {{showTipText}}
            </view>
            </AtInput>
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
import { AtInput, AtForm } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

export default {
  components: {
    DocsHeader,
    AtInput,
    AtForm
  },
  data() {
    return {
      value1: '',
      value2: '',
      value3: '',
      value4: '',
      value5: '',
      value6: '',
      value7: '',
      value8: '',
      value9: '',
      value10: '',
      value11: '',
      value13: '',
      value14: '',
      value15: '',
      value16: '',
      value17: '',
      disabled: false,
      second: 60,
      verificationCode: require("../../../assets/images/verification_code.png")
    }
  },
  computed: {
    showTipText() {
      return this.disabled ? `${this.second}s后重试` : '发送验证码'
    }

  },
  mounted() {
  },
  methods: {
    handleInput(stateName, value) {
      this[stateName] = value;
    },
    onClickErrorIcon() {
      Taro.showToast({
        title: '请输入数字',
        icon: 'success',
        duration: 2000
      })
    },
    handleKeyboardHeightChange() {
      Taro.showToast({
      title: `高度 ${event.detail.height}`,
      icon: 'success',
      duration: 2000
      });
    },
    sendCode() {
      if (this.disabled) return
      this.disabled = true;
      // 倒计时
      const timer = setInterval(() => {
        if (this.second > 0) {
          this.second = this.second - 1;
        } else {
          this.second = 60;
          this.disabled = false;
          clearInterval(timer)
        }
      }, 1000)
    }
  }
}
</script>
