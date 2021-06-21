<template>
  <view class='page'>
    <DocsHeader title='Pagination 分页器'></DocsHeader>

    <view class='doc-body'>
      <!--   基础用法   -->
      <view class='panel'>
        <view class='panel__title'>基础用法</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtPagination
              :total="20"
              :pageSize="10"
              :current="1"
            ></AtPagination>
          </view>
        </view>
      </view>

      <!--   图标类型   -->
      <view class='panel'>
        <view class='panel__title'>图标类型</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtPagination
              icon
              :total="20"
              :pageSize="10"
              :current="1"
            ></AtPagination>
          </view>
        </view>
      </view>

      <!--   点击页码出是否出现picker选择页码   -->
      <view class='panel'>
        <view class='panel__title'>picker快速选择页码</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtPagination
              icon
              :total="20"
              :pageSize="10"
              :current="1"
            ></AtPagination>
          </view>
        </view>
      </view>

      <!--   改变数据长度   -->
      <view class='panel'>
        <view class='panel__title'>改变数据长度</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtPagination
              icon
              :total="len"
              :pageSize="pageSize"
              :current="current"
              :onPageChange="this.onPage.bind(this)"
            ></AtPagination>
            <view class='btn-item'>
              当前页：{{ current }}，当前数据：{{ len }}条，分页大小：
              {{ pageSize }}
            </view>
            <view class='btn-item'>
              <AtButton
                type='primary'
                :onClick="this.onPageDataChange.bind(this)"
              >
                增加10条数据
              </AtButton>
            </view>
            <view class='btn-item'>
              <AtButton :onClick="this.onCurrentChange.bind(this)">
                重置
              </AtButton>
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
import { AtPagination, AtButton } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

export default {
  components: {
    DocsHeader,
    AtPagination,
    AtButton
  },
  data() {
    return {
      list: [],
      current: 1,
      pageSize: 10
    }
  },
  computed: {
    len() {
      return this.list.length;
    }
  },
  mounted() {
  },
  methods: {
    onPage(data) {
      this.current = data.current;
      Taro.showToast({
        title: `Pagination: ${data}`,
        icon: 'none'
      })
    },
    onPageDataChange() {
      const _list = new Array(10).fill(1);
      this.list = this.list.concat(_list)
    },
    onCurrentChange() {
      this.current = 1;
      this.list = [];
    }
  }
}
</script>
