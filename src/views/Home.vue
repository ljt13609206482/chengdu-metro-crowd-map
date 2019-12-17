<!-- 拥挤度地图 -->
<template>
  <div class="container">
    <div class="subway-map">
      <subway
        :lines="lines"
        :view-box="viewBox"
        :stations="stations"
        :stations-limit="stationsLimit"
        :stations-ex-limit="stationsExLimit"
        :texts="texts"
        :station-exs="stationExs"
      />
    </div>
    <!-- <div class="bottom-box">
      <div class="legend-box">
        <div class="legend-item item-left-box">
          <div class="color-box blocking" />
          <div class="legend-text tip-text">
            <p>拥挤</p>
            <p>繁忙</p>
            <p>舒适</p>
          </div>
        </div>
        <div class="legend-item item-right-box">
          <div class="nonactivated" />
          <div class="legend-text">限流</div>
        </div>
      </div>
      <div class="bottom-text">
        <div class="left-box">此数据仅供参考</div>
        <div class="right-box">数据时间：{{ nowDate }}</div>
      </div>
    </div> -->
  </div>
</template>

<script>
import data from "../../public/data/cdmetro-subway";
import Subway from "./Subway/Subway";
// import api from "../../service/api.js";

export default {
  components: {
    Subway
  },

  data() {
    return {
      lines: {},
      viewBox: {},
      stations: {},
      stationExs: [],
      stationsLimit: {},
      stationsExLimit: {},
      texts: [],
      showStatus: [],
      nowDate: ""
    };
  },
  // created() {
  //   let timer = setInterval(() => {
  //     this.get_data();
  //     this.get_limit_stations();
  //   }, 60000);
  // },
  computed: {
    allStations() {
      return {
        stations: this.stations,
        stationExs: this.stationExs,
        stationsLimit: this.stationsLimit,
        stationsExLimit: this.stationsExLimit
      };
    }
  },
  async mounted() {
    this.lines = data.lines;
    this.stations = data.stations;
    this.stationExs = data.stationEx;
    this.texts = data.texts;
    this.viewBox = {
      width: data.width,
      height: data.height
    };
    // this.get_data();
    // this.get_limit_stations();
  },

  methods: {
    // get_data() {
    //   let date = new Date().format("MM-dd hh:mm:ss");
    //   this.nowDate = date;
    //   api.crowd_data().then(res => {
    //     let crowdData = res.list;
    //     let topicData = crowdData.filter(item => {
    //       return item.SECTIONLOAD >= 0.6;
    //     });
    //     for (let i in topicData) {
    //       let dataItem = topicData[i];
    //       let curLineList = this.lines.lineList[
    //         parseInt(dataItem.LINECODE) - 1
    //       ];
    //       curLineList.paths.forEach(pathItem => {
    //         if (pathItem.id == dataItem.SECTIONCODE) {
    //           if (
    //             0.6 < parseFloat(dataItem.SECTIONLOAD) &&
    //             parseFloat(dataItem.SECTIONLOAD) < 0.8
    //           ) {
    //             this.$nextTick(() => {
    //               this.$set(pathItem, "color", "#e6bf00");
    //             });
    //           } else if (
    //             0.8 < parseFloat(dataItem.SECTIONLOAD) &&
    //             parseFloat(dataItem.SECTIONLOAD) < 1.0
    //           ) {
    //             this.$nextTick(() => {
    //               this.$set(pathItem, "color", "#ed7900");
    //             });
    //           } else if (1.0 < parseFloat(dataItem.SECTIONLOAD)) {
    //             this.$nextTick(() => {
    //               this.$set(pathItem, "color", "#e02f24");
    //             });
    //           }
    //         }
    //       });
    //     }
    //   });
    // },
    // get_limit_stations() {
    //   api.get_limit_stations().then(response => {
    //     if (response.code == 0) {
    //       let limitData = response.data;
    //       let limitArr = [];
    //       let limitExArr = [];
    //       limitData.map(ele => {
    //         let stationLimitItem = data.stationsLimit.list.filter(item => {
    //           return item.id == ele;
    //         });
    //         if (stationLimitItem.length > 0) {
    //           limitArr.push(stationLimitItem[0]);
    //         }
    //         let stationExLimitItem = data.stationsExLimit.list.filter(item => {
    //           let idArr = item.id.split(",");
    //           if (idArr.indexOf(ele) > -1) {
    //             return item;
    //           }
    //         });
    //         if (stationExLimitItem.length > 0) {
    //           limitExArr.push(stationExLimitItem[0]);
    //         }
    //       });
    //       let stationLimitData = data.stationsLimit;
    //       let stationExLimitData = data.stationsExLimit;
    //       data.stationsLimit.list = limitArr;
    //       data.stationsExLimit.list = limitExArr;
    //       this.stationsLimit = stationLimitData;
    //       this.stationsExLimit = stationExLimitData;
    //     } else {
    //       Toast(res.message);
    //     }
    //   });
    // }
  }
};
</script>
<style scoped>
.container {
  width: 100%;
  height: 100%;
  position: relative;
}
.container .subway-map {
  width: 100%;
  height: 100%;
}
/* .container .bottom-box {
  margin: 1.25rem;
  padding: 10px 10px;
  box-sizing: border-box;
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: #ffffff;
  border-radius: 0.5rem;
  box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
.container .bottom-box .bottom-text {
  padding-top: 4px;
  font-size: 10px;
  color: #666666;
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
}
.bottom-box .left-box {
  width: 40%;
}
.bottom-box .right-box {
  width: 60%;
  text-align: right;
}
.container .legend-box {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
  padding-bottom: 4px;
  border-bottom: 1px solid #f4f4f4;
}
.legend-box .item-left-box {
  width: 90%;
  padding-right: 1rem;
  box-sizing: border-box;
}
.legend-box .item-right-box {
  text-align: center;
}
.legend-box .legend-item .color-box {
  margin: 0 auto;
  width: 100%;
  height: 0.8rem;
  font-size: 10px;
  border-radius: 1px;
}

.legend-box .legend-item .blocking {
  background: url("../../assets/crowd-map/color.png") no-repeat;
  background-size: 100% 100%;
  background-position: center center;
}
.legend-box .legend-item .crowded {
  background-color: #ed7900;
}
.legend-box .legend-item .busy {
  background-color: #e6bf00;
}
.legend-box .legend-item .comfortable {
  background-color: #22b312;
}
.legend-box .legend-item .nodata {
  background-color: #435263;
}
.legend-box .legend-item .nonactivated {
  width: 0.8rem;
  height: 0.8rem;
  margin: 0 auto;
  background: url("../../assets/crowd-map/logo.png");
  background-size: 100% 100%;
  background-position: center center;
}
.legend-box .legend-item .legend-text {
  margin-top: 0.5rem;
  font-size: 12px;
}
.legend-item .tip-text {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
} */
</style>
