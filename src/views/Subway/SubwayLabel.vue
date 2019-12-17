<style lang='stylus'>

</style>
<template>
  <g :id="data.id" :transform="data.transform" :fill="data.fill" :fill-rule="data.fillRule">
    <g
      v-for="(item, index) in data.textList"
      :id="item.id"
      :key="index"
      :transform="item.transform"
    >
      <path v-for="(pathItem, index2) in item.path" :key="index2" :d="pathItem.d" :di="pathItem.id" />
    </g>
  </g>
</template>

<script>
export default {
  components: {},

  props: {
    data: {
      type: Object,
      default: () => {}
    }
  },

  data() {
    return {};
  },

  computed: {},

  mounted() {
  },

  methods: {}
};
</script>
