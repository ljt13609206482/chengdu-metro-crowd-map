<style lang='stylus'>

</style>
<template>
  <g :id="data.id" :transform="data.transform" :fill="data.fill" :stroke-width="data['stroke-width']" :stroke="data['stroke']">
    <g
      v-for="(item, index) in data.stationList"
      :key="index"
      :id="item.id"
      :transform="item.transform"
    >
      <template >
        <g v-for="(stationItme, index2) in item.circle" :data-id="stationItme.id" :key="index2">
          <circle  :cx="stationItme.cx" :cy="stationItme.cy" :r="stationItme.r"/>
        </g>
      </template>
    </g>
  </g>
</template>

<script>
export default {
  components: {},
  props: {
    data: ''
  },

  data() {
    return {};
  },

  computed: {},

  mounted() {},

  methods: {
  }
};
</script>
