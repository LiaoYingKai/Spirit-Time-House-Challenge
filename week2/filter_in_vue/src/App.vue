<template>
<div id="app">
  <Header/>
  <div class="content">
    <FilterBar v-bind:location="location" v-on:userSelected="getSelected" />
    <Content v-bind:attractionData="filterAttraction" v-bind:userSelected="userSelected" v-on:userSelected="getSelected" class="style" />
  </div>
</div>
</template>

<script>
import Header from './components/Header'
import FilterBar from './components/FilterBar'
import Content from './components/Content'
import axios from "axios";

export default {
  name: 'App',
  components: {
    Header,
    FilterBar,
    Content
  },
  data() {
    return {
      attractionData: [],
      filterAttraction: [],
      location: [],
      apiData: [],
      userSelected: ''
    }
  },
  mounted: function() {
    axios.get(`https://data.kcg.gov.tw/api/action/datastore_search?resource_id=92290ee5-6e61-456f-80c0-249eae2fcc97`)
      .then(promise => {
        this.apiData = promise.data.result.records
        this.apiData.forEach(item => {
          if (this.location.indexOf(item.Zone) === -1) {
            this.location.push(item.Zone)
          }
        })
        this.attractionData = this.apiData
        this.filterAttraction = this.apiData
      })
      .catch(err => {
        console.log(err)
      })
  },
  methods: {
    getSelected: function(data) {
      this.userSelected = data
      this.filterCondition(data)
    },
    filterCondition: function(condition) {
      this.filterAttraction = []
      if (condition === "---") {
        this.filterAttraction = this.attractionData
      } else {
        this.attractionData.forEach(item => {
          if (item.Zone === condition) {
            this.filterAttraction.push(item)
          }
        })
      }
    }
  }
}
</script>

<style>
body {
  margin: 0;
  background-color: #F2F2F2;
}

.content {
  width: 1200px;
  margin: 0 auto;
  padding: 0 38px;
  display: flex;
}

.style {
  margin-left: 110px;
  margin-top: 24px;
}
</style>
