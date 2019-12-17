<style lang='stylus'>
</style>
<template>
  <g>
    <g v-for="(item,index) in data" :id="item.id" :transform="item.transform" :key="index">
    <g>
      <circle v-for="(circle,index1) in item.circle" :key="index1" :id="circle.id" :stroke="circle.stroke" :stroke-width="circle['stroke-width']" :fill="circle.fill" :cx="circle.cx" :cy="circle.cy" :r="circle.r"></circle>
    </g>
    <g>
      <path v-for="(path,index2) in item.path" :key="index2" :d="path.d" :id="path.id" :fill="path.fill" :fill-rule="path.fillRule"></path>
    </g>
  </g>
  </g>
</template>

<script>
export default {
  components: {},
  props: {
    data: Array
  },

  data() {
    return {};
  },

  computed: {},

  mounted() {},

  methods: {
    show(item) {
      console.log(item);
    }
  }
};
</script>
