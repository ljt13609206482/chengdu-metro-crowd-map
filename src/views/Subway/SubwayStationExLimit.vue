<!-- 换乘站点限流 -->
<style lang='stylus'>

</style>
<template>
  <g>
    <g :id="data.id" :transform="data.transform">
    <g v-for="(item1,index1) in data.list" :id="item1.id" :key="index1" :transform="item1.transform">
      <circle :id="item1.circle.id" :stroke="item1.circle.stroke" :stroke-width="item1.circle['stroke-width']" :fill="item1.circle.fill" :cx="item1.circle.cx" :cy="item1.circle.cy" :r="item1.circle.r" />

      <rect :id="item1.rect.id" :fill="item1.rect.fill" :width="item1.rect.width" :height="item1.rect.height" :x="item1.rect.x" :y="item1.rect.y" />
    </g>
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

  methods: {
  }
};
</script>
