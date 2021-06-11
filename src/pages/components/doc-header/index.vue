<template>
  <view class="doc-header">
    <view class='doc-header__title'>{{ title }}</view>
  </view>
</template>
<script>
import './index.scss'

export default {
  name: "doc-header",
  props: {
    title: {type: String, default: ''}
    },
};

</script>
