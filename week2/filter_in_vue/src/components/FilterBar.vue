<template >
<div class="filterBar">
  <div class="location">
    Location
    <div class="locationContent">
      <select v-model="selected" v-on:change="getSelected">
        <option>---</option>
        <option v-for="item in location" >{{item}}</option>
      </select>
    </div>
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      selected: ''
    }
  },
  props: ["location"],
  methods: {
    getSelected: function() {
      this.$emit("userSelected", this.selected)
    },
  }
}
</script>

<style lang="scss" scoped>
@import "minix";
.filterBar {
    width: 300px;
    height: 132px;
    background-color: #EBEBEB;
}
.location {
    @include filterStyle;
    .locationContent {
        margin-top: 20px;
        select {
            height: 40px;
            width: 100%;
            border: 1px #fff solid;
            border-radius: 2px;
            background-color: #fff;
            font-size: 16px;
            line-height: 19px;
        }
    }
}
</style>
