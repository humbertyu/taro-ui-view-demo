<template>
  <view class='page'>
    <DocsHeader title='ImagePicker 图片选择器'></DocsHeader>

    <view class='doc-body'>
      <!--   基础用法   -->
      <view class='panel'>
        <view class='panel__title'>基础用法</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtImagePicker
              :files="files1"
              :onChange="this.onChange.bind(this, 'files1')"
            />
          </view>
        </view>
      </view>

      <!--   多选图片   -->
      <view class='panel'>
        <view class='panel__title'>多选图片</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtImagePicker
              multiple
              :files="files2"
              :onChange="this.onChange.bind(this, 'files2')"
              :onFail="this.onFail.bind(this)"
              :onImageClick="this.onImageClick.bind(this)"
            />
          </view>
        </view>
      </view>

      <!--   自定义每行数量   -->
      <view class='panel'>
        <view class='panel__title'>自定义每行数量</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtImagePicker
              multiple
              :length="3"
              :files="files3"
              :onChange="this.onChange.bind(this, 'files3')"
            />
          </view>
        </view>
      </view>

      <!--   更改图片的缩放模式   -->
      <view class='panel'>
        <view class='panel__title'>更改图片的缩放模式</view>
        <view class='panel__content no-padding'>
          <view class='example-item'>
            <AtImagePicker
              mode='aspectFit'
              multiple
              :files="files4"
              :onChange="this.onChange.bind(this, 'files4')"
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
import { AtImagePicker } from 'taro-ui-vue'
import Taro from '@tarojs/taro'

const dotaImags = [
                    {
                      url: 'https://storage.360buyimg.com/mtd/home/111543234387022.jpg'
                    },
                    {
                      url: 'https://storage.360buyimg.com/mtd/home/221543234387016.jpg'
                    },
                    {
                      url: 'https://storage.360buyimg.com/mtd/home/331543234387025.jpg'
                    },
                    {
                      type: 'btn'
                    }
                  ];
export default {
  components: {
    DocsHeader,
    AtImagePicker
  },
  data() {
    return {
      files1: [...dotaImags],
      files2: [...dotaImags],
      files3: [...dotaImags],
      files4: [...dotaImags].concat([
        {
          url:
            'https://storage.360buyimg.com/mtd/home/36549825_887087111478302_5745542532574478336_n1543234831971.jpg'
        }
      ])
    }
  },
  computed: {
  },
  mounted() {
  },
  methods: {
    onChange(stateName, files) {
      this[stateName] = files;
    },
    onFail(mes) {
      Taro.showToast({
        title: `onFail: ${mes}`,
        icon: 'none'
      })
    },
    onImageClick(index, file) {
      Taro.showToast({
        title: `onImageClick: ${index}${file}`,
        icon: 'none'
      })
    }
  }
}
</script>
