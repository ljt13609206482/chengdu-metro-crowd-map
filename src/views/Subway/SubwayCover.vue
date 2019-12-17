<style lang='stylus'>

</style>
<template>
  <g>
    <g id="station-cover" transform="translate(-40 53)">
      <g v-if="item.coverX&&item.coverY" v-for="(item, index) in stations" :key="index" :data-name="item.name"
        :transform="`translate(${item.coverX} ${item.coverY})`">
        <template>
          <circle v-if="item.status === 1" fill="url(#grad1)" class='dot-style' cx="10" cy="10" r="10" @mouseenter="show(item)">
            <animate id='ani1' attributeName='fill-opacity' attributeType='XML' begin='0s;ani2.end' dur='1s' from='1'
              to='0.4' fill='freeze' />
            <animate id='ani2' attributeName='fill-opacity' attributeType='XML' begin='ani1.end' dur='1s' from='0.4' to='1'
              fill='freeze' />
          </circle>
          <circle v-if="item.status === 2" fill="url(#grad1)" class='dot-style' cx="15" cy="15" r="15" @mouseenter="show(item)">
            <animate id='ani1' attributeName='fill-opacity' attributeType='XML' begin='0s;ani2.end' dur='1s' from='1'
              to='0.4' fill='freeze' />
            <animate id='ani2' attributeName='fill-opacity' attributeType='XML' begin='ani1.end' dur='1s' from='0.4' to='1'
              fill='freeze' />
          </circle>
          <circle v-if="item.status === 3" fill="url(#grad1)" class='dot-style' cx="20" cy="20" r="20" @mouseenter="show(item)">
            <animate id='ani1' attributeName='fill-opacity' attributeType='XML' begin='0s;ani2.end' dur='1s' from='1'
              to='0.4' fill='freeze' />
            <animate id='ani2' attributeName='fill-opacity' attributeType='XML' begin='ani1.end' dur='1s' from='0.4' to='1'
              fill='freeze' />
          </circle>
          <circle v-if="item.status === 4" fill="url(#grad1)" class='dot-style' cx="25" cy="25" r="25" @mouseenter="show(item)">
            <animate id='ani1' attributeName='fill-opacity' attributeType='XML' begin='0s;ani2.end' dur='1s' from='1'
              to='0.4' fill='freeze' />
            <animate id='ani2' attributeName='fill-opacity' attributeType='XML' begin='ani1.end' dur='1s' from='0.4' to='1'
              fill='freeze' />
          </circle>
        </template>
      </g>
    </g>
    <g id="station-ex-cover" transform="translate(2)">
      <g v-if="item.coverX&&item.coverY" v-for="(item, index) in stationExs" :key="index" :data-name="item.name"
        :transform="`translate(${item.coverX} ${item.coverY})`">
        <defs>
          <radialGradient id="grad1" cx="50%" cy="50%" r="50%" fx="50%" fy="50%">
            <stop offset="0%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
            <stop offset="70%" style="stop-color:rgb(255,0,0);stop-opacity:0.8" />
            <stop offset="100%" style="stop-color:rgb(255,255,255);stop-opacity:1" />
          </radialGradient>
        </defs>
        <template>
          <circle v-if="item.status === 1" fill="url(#grad1)" class='dot-style' cx="10" cy="10" r="10" @mouseenter="show(item)">
            <animate id='ani1' attributeName='fill-opacity' attributeType='XML' begin='0s;ani2.end' dur='1s' from='1'
              to='0.4' fill='freeze' />
            <animate id='ani2' attributeName='fill-opacity' attributeType='XML' begin='ani1.end' dur='1s' from='0.4' to='1'
              fill='freeze' />
          </circle>
          <circle v-if="item.status === 2" fill="url(#grad1)" class='dot-style' cx="15" cy="15" r="15" @mouseenter="show(item)">
            <animate id='ani1' attributeName='fill-opacity' attributeType='XML' begin='0s;ani2.end' dur='1s' from='1'
              to='0.4' fill='freeze' />
            <animate id='ani2' attributeName='fill-opacity' attributeType='XML' begin='ani1.end' dur='1s' from='0.4' to='1'
              fill='freeze' />
          </circle>
          <circle v-if="item.status === 3" fill="url(#grad1)" class='dot-style' cx="20" cy="20" r="20" @mouseenter="show(item)">
            <animate id='ani1' attributeName='fill-opacity' attributeType='XML' begin='0s;ani2.end' dur='1s' from='1'
              to='0.4' fill='freeze' />
            <animate id='ani2' attributeName='fill-opacity' attributeType='XML' begin='ani1.end' dur='1s' from='0.4' to='1'
              fill='freeze' />
          </circle>
          <circle v-if="item.status === 4" fill="url(#grad1)" class='dot-style' cx="25" cy="25" r="25" @mouseenter="show(item)">
            <animate id='ani1' attributeName='fill-opacity' attributeType='XML' begin='0s;ani2.end' dur='1s' from='1'
              to='0.4' fill='freeze' />
            <animate id='ani2' attributeName='fill-opacity' attributeType='XML' begin='ani1.end' dur='1s' from='0.4' to='1'
              fill='freeze' />
          </circle>
        </template>
      </g>
    </g>
  </g>
</template>

<script>
export default {
  components: {},
  props: {
    data: Object
  },

  data() {
    return {};
  },

  computed: {
    stations() {
      const stations = this.data.stations;
      stations.stationList.map(item => {
        item.x = item.x || 0;
        item.y = item.y || 0;
        if (item.status === 1) {
          item.coverX = item.x - 4;
          item.coverY = item.y - 4;
        }
        if (item.status === 2) {
          item.coverX = item.x - 10;
          item.coverY = item.y - 10;
        }
        if (item.status === 3) {
          item.coverX = item.x - 12.5;
          item.coverY = item.y - 15;
        }
        if (item.status === 4) {
          item.coverX = item.x - 17.5;
          item.coverY = item.y - 20;
        }
      });
      return stations;
    },
    stationExs() {
      const stations = this.data.stationExs;
      stations.stationList.map(item => {
        item.x = item.x || 0;
        item.y = item.y || 0;
        if (item.status === 1) {
          item.coverX = item.x + 2;
          item.coverY = item.y - 3;
        }
        if (item.status === 2) {
          item.coverX = item.x - 4;
          item.coverY = item.y - 10;
        }
        if (item.status === 3) {
          item.coverX = item.x - 10;
          item.coverY = item.y - 15;
        }
        if (item.status === 4) {
          item.coverX = item.x - 12.5;
          item.coverY = item.y - 20;
        }
      });
      return stations;
    }
  },

  mounted() { },

  methods: {
    show(item) {
      console.log(item);
    }
  }
};
</script>
