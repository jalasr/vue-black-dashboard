<template>
  <div class="card" :class="[type && `card-${type}`]">
    <div class="card-image" v-if="$slots.image">
      <slot name="image"></slot>
    </div>
    <div class="card-header" :class="{'text-right': isRTL}" v-if="$slots.header || title">
      <slot name="header">
        <h4 class="card-title">{{title}}</h4>
        <p class="card-category" v-if="subTitle">{{subTitle}}</p>
      </slot>
    </div>
    <div class="card-body" v-if="$slots.default">
      <slot></slot>
    </div>
    <slot name="raw-content"></slot>
    <div class="card-footer" v-if="$slots.footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>
<script>
export default {
  name: "card",
  props: {
    title: String,
    subTitle: String,
    type: String
  },
  computed: {
    isRTL() {
      return this.$rtl.isRTL;
    }
  }
};
</script>
<style>
</style>
