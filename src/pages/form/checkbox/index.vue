<template>
  <view class='page'>
    <DocsHeader title='Checkbox 复选框'></DocsHeader>

    <view class='doc-body'>
      <!--   基础用法   -->
      <view class='panel'>
        <view class='panel__title'>基础用法</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <view class='checkbox-container'>
              <AtCheckbox
                :options="checkboxOption1"
                :selectedList="checkedList1"
                :onChange="this.handleChange.bind(this)"
              />
            </view>
          </view>
        </view>
      </view>

      <!--   含描述信息   -->
      <view class='panel'>
        <view class='panel__title'>含描述信息</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <view class='checkbox-container'>
              <AtCheckbox
                :options="checkboxOption2"
                :selectedList="checkedList2"
                :onChange="this.handleChangeSnd.bind(this)"
              />
            </view>
          </view>
        </view>
      </view>

      <!--   选项禁用   -->
      <view class='panel'>
        <view class='panel__title'>选项禁用</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <view class='checkbox-container'>
              <AtCheckbox
                :options="checkboxOption3"
                :selectedList="checkedList3"
                :onChange="this.handleChangeThd.bind(this)"
              />
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
import { AtCheckbox } from 'taro-ui-vue'

export default {
  components: {
    DocsHeader,
    AtCheckbox
  },
  data() {
    return {
      checkedList1: ['list1'],
      checkedList2: ['list1'],
      checkedList3: ['list1', 'list4'],
      checkboxOption1: [
        { value: 'list1', label: 'iPhone X' },
        { value: 'list2', label: 'HUAWEI P20' },
        { value: 'list3', label: 'OPPO Find X' }
      ],
      checkboxOption2: [
        {
          value: 'list1',
          label: 'iPhone X',
          desc:
            '部分地区提供电子普通发票，用户可自行打印，效力等同纸质普通发票，具体以实际出具的发票类型为准。'
        },
        {
          value: 'list2',
          label: 'HUAWEI P20',
          desc:
            '部分地区提供电子普通发票，用户可自行打印，效力等同纸质普通发票，具体以实际出具的发票类型为准。'
        },
        {
          value: 'list3',
          label: 'OPPO Find X',
          desc:
            '部分地区提供电子普通发票，用户可自行打印，效力等同纸质普通发票，具体以实际出具的发票类型为准。'
        }
      ],
      checkboxOption3: [
        {
          value: 'list1',
          label: 'iPhone X',
          desc:
            '部分地区提供电子普通发票，用户可自行打印，效力等同纸质普通发票，具体以实际出具的发票类型为准。'
        },
        { value: 'list2', label: 'HUAWEI P20' },
        {
          value: 'list3',
          label: 'OPPO Find X',
          desc:
            '部分地区提供电子普通发票，用户可自行打印，效力等同纸质普通发票，具体以实际出具的发票类型为准。',
          disabled: true
        },
        {
          value: 'list4',
          label: 'vivo NEX',
          desc:
            '部分地区提供电子普通发票，用户可自行打印，效力等同纸质普通发票，具体以实际出具的发票类型为准。',
          disabled: true
        }
      ]
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    handleChange(value) {
      this.checkedList1 =value;
    },
    handleChangeSnd(value) {
      this.checkedList2 = value;
    },
    handleChangeThd(value) {
      this.checkedList3 = value;
    }
  }
}
</script>
