<style lang='stylus'>
</style>
<template>
  <g :id="lineData.id" :transform="lineData.transform" :fill="lineData.fill">
    <template v-for="item in lineData.lineList">
      <g v-if="item.paths" :id="item.id" :key="item.id" :transform="item.transform">
        <path v-for="path in item.paths" :id="path.id" :key="path.id" :d="path.d" :fill="path.color" :transform="path.transform" />
      </g>
      <path v-else :id="item.id" :key="item.id" :transform="path.transform" :d="item.d" :fill="item.color" />
    </template>
  </g>
</template>

<script>
export default {
  components: {},

  props: {
    width: {
      type: Number,
      default: () => {}
    },
    height: {
      type: Number,
      default: () => {}
    },
    lineData: {
      type: Object,
      default: () => {}
    }
  },

  data() {
    return {
      cData: ""
    };
  },
  computed: {

  },
  watch: {
    "lineData": (newVal, oldVal) => {
      this.cData = newVal;
      // console.log(this.cData)
    },
    deep: true
  },

  mounted() {
  },

  methods: {

  }
};
</script>
