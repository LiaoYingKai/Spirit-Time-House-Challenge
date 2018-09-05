<template >
<div class="filter">
  <p v-if="whenterFilter">Showing <span>{{attractionData.length}}</span> result by...</p>
  <div class="filterCondition">
    <div class="filterConditionStyle" v-if="whenterFilter">
      {{userSelected}}
      <font-awesome-icon icon="times-circle" v-on:click="cancelFilter" />
    </div>
  </div>
  <div class="filterAttraction" v-for="item in attractionData">
    <img :src="`${item.Picture1}`" alt="">
    <div class="attractionContent">
      <div class="attractionName">
        {{item.Name}}
      </div>
      <div class="attractionText">
        {{item.Description}}
      </div>
      <div class="attractionAddress">
        地址：{{item.Add}}
      </div>
      <div class="attractionOpentime">
        開放時間：{{item.Opentime}}
      </div>
      <div class="attractionFare">
        票價資訊：{{item.Ticketinfo}}
      </div>

    </div>
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      whenterFilter: false
    }
  },
  props: ["attractionData", "userSelected"],
  watch: {
    userSelected: function() {
      if (this.userSelected === "---") {
        this.whenterFilter = false
      } else {
        this.whenterFilter = true
      }
    }
  },
  methods: {
    cancelFilter: function() {
      this.$emit("userSelected", "---")
      this.whenterFilter = false
      // console.log("fuck")
    }
  }
}
</script>

<style lang="scss" scoped>
.filter {
    font-size: 24px;
    font-family: sans-serif;
    color: #000;
    p {
        margin: 0;
    }
    span {
        color: #9013FE;
    }
}
.filterCondition {
    display: flex;
    margin-top: 8px;
    .filterConditionStyle {
        padding: 8px 16px;
        border: 1px solid #9013FE;
        border-radius: 100px;
        color: #9013FE;
        font-size: 16px;
        &:hover {
            background-color: #9013FE;
            color: #fff;
        }
        .fa-times-circle {
            cursor: pointer;
            margin-left: 8px;
        }
    }
}
.filterAttraction {
    margin-top: 24px;
    width: 780px;
    img {
        height: auto;
        width: 100%;
    }
}
.attractionContent {
    margin-top: 24px;
    .attractionName {
        font-family: sans-serif;
        font-size: 24px;
        color: #9013FE;
        line-height: 36px;
    }
    .attractionText {
        margin-top: 16px;
        font-family: sans-serif;
        font-size: 16px;
        color: #000000;
        line-height: 24px;
    }
    .attractionAddress,
    .attractionFare,
    .attractionOpentime {
        font-family: sans-serif;
        font-size: 16px;
        margin-top: 16px;
    }
}
</style>
