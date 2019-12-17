<style lang='stylus'>
.subway {
  position: relative;
  width: 100%;
  height: 100%;
  // overflow: hidden;

  .svg-box {
    width: 100%;
    left: 0%;
    top: 30%;
    position: absolute;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    -webkit-user-drag: none;
  }

  @media only screen and (max-width: 340px) {
    .svg-box {
      top: 40%;
    }
  }

  @media only screen and (device-width: 375px) and (device-height: 812px) and (-webkit-device-pixel-ratio: 3) {
    .svg-box {
      top: 24%;
    }
  }

  svg {
    width: 100%;
    position: absolute;
    left: 0;
    top: 0;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    -webkit-user-drag: none;
  }

  .pinch-zoom {
    width: 100%;
    height: 100%;
    -webkit-user-drag: none;
  }

  .subway-stations {
    z-index: 20;
  }

  .subway-line {
    z-index: 10;
  }

  .subway-label {
    z-index: 30;
  }

  .subway-bg {
    z-index: -1;
  }
}
</style>
<template>
  <div id="subway-box" class="subway">
    <div class="pinch-zoom">
      <div id="svg-box" class="svg-box">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" :viewBox="`0 0 ${viewBox.width||0} ${viewBox.height||0}`">
          <g id="cdmetro" transform="translate(0 0)">
            <subway-line :lineData="lines" />
            <subway-station :data="stations" />
            <subway-ex-station :data="stationExs" />
            <subway-station-limit :data="stationsLimit" />
            <subway-station-ex-limit :data="stationsExLimit" />
            <subway-label :data="texts" />
            <subway-introduce />
          </g>
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
import SubwayIntroduce from "./SubwayIntroduce";
import SubwayLine from "./SubwayLine";
import SubwayStation from "./SubwayStation";
import SubwayExStation from "./SubwayExStation";
import SubwayLabel from "./SubwayLabel";
import SubwayStationLimit from "./SubwayStationLimit";
import SubwayStationExLimit from "./SubwayStationExLimit";
export default {
  components: {
    SubwayIntroduce,
    SubwayLine,
    SubwayStation,
    SubwayExStation,
    SubwayLabel,
    SubwayStationLimit,
    SubwayStationExLimit
  },
  props: {
    viewBox: {
      type: Object,
      require: false,
      default: () => {}
    },
    lines: {
      type: Object,
      require: false,
      default: () => {}
    },
    stations: {
      type: Object,
      require: false,
      default: () => {}
    },
    stationExs: {
      type: Array,
      require: false,
      default: () => {}
    },
    stationsLimit: {
      type: Object,
      require: false,
      default: () => {}
    },
    stationsExLimit: {
      type: Object,
      require: false,
      default: () => {}
    },
    texts: {
      type: Object,
      require: false,
      default: () => {}
    }
  },
  data() {
    return {
      boxWidth: "100",
      topPosition: "-0",
      leftPosition: "-0"
    };
  },

  computed: {
    allStations() {
      return { stations: this.stations, stationExs: this.stationExs, stationsLimit: this.stationsLimit, stationsExLimit: this.stationsExLimit };
    }
  },

  mounted() {
    // console.log(this.texts);
    // $(function () {
    //   $('div.pinch-zoom').each(function () {
    //     new RTP.PinchZoom($(this), {});
    //   });
    // });
  },

  methods: {

  }
};
</script>
