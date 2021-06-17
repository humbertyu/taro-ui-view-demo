<template>
  <view class='page'>
    <DocsHeader title='Form 表单'></DocsHeader>

    <view class='doc-body'>
      <!--   表单提交与重置   -->
      <view class='panel'>
        <view class='panel__title'>表单提交与重置</view>
        <view class='panel__content no-padding'>
          <view class='component-item'>
            <AtForm
              :onSubmit="this.handleSubmit.bind(this)"
              :onReset="this.handleReset.bind(this)"
            >
              <AtInput
                required
                name='value1'
                title='文本'
                type='text'
                placeholder='单行文本'
                :value="value1"
                :onChange="this.handleChange.bind(this, 'value1')"
              />
              <AtInput
                required
                name='value2'
                title='密码'
                type='password'
                placeholder='请输入密码'
                :value="value2"
                :onChange="this.handleChange.bind(this, 'value2')"
              />
              <AtCheckbox
                :options="[
                    { label: 'iPhone X', value: 'iPhone X' },
                    { label: 'HUAWEI P20', value: 'HUAWEI P20' }
                ]"
                :selectedList="value3"
                :onChange="this.handleChange.bind(this, 'value3')"
              />
              <view class='component-item__btn-group'>
                <view class='component-item__btn-group__btn-item'>
                  <AtButton type='primary' formType='submit'>
                    提交
                  </AtButton>
                </view>
                <view class='component-item__btn-group__btn-item'>
                  <AtButton formType='reset'>重置</AtButton>
                </view>
              </view>
            </AtForm>
          </view>
        </view>
      </view>
    </view>
    <AtToast
      :text="text"
      :isOpened="isOpened"
    ></AtToast>
  </view>
</template>
<script>
import DocsHeader from '../../components/doc-header/index'
import './index.scss'
import { AtToast, AtForm, AtInput, AtCheckbox, AtButton } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtToast,
    AtForm,
    AtInput,
    AtCheckbox,
    AtButton
  },
  data() {
    return {
      value1: '',
      value2: '',
      value3: [],
      text: '',
      isOpened: false
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    handleChange(stateName, value) {
      this[stateName] = value;
    },
    closeToast() {
      setTimeout(() => {
        this.isOpened = false;
      }, 2000)
    },
    handleSubmit() {
      if (!this.value1 || !this.value2) {
        this.isOpened = true;
        this.text = '表单必填项未填写完整';
      } else {
        this.isOpened = true;
        this.text = this.value3 && this.value3.length > 0
          ? `${this.value1} / ${this.value2} / ${this.value3.join(',')}`
          : `${this.value1} / ${this.value2}`;
      }
      this.closeToast()
    },
    handleReset() {
      this.isOpened = true;
      this.text = '表单已被重置';
      this.value1 = '';
      this.value2 = '';
      this.value3 = [];
      this.closeToast()
    }
  }
}
</script>
