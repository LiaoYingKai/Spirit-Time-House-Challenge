<template>
<div class="header">
  <div class="logo">
    HaveFun
  </div>
  <div class="inputBar">
    <font-awesome-icon icon="search" />
    <input type="text" placeholder="Explore your own activited">
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {}
  }
}
</script>

<style lang="scss" scoped>
.header {
    width: 1200px;
    margin: 0 auto;
    background-color: #7828B4;
    display: flex;
    align-items: center;
    padding: 24px 0;
}
.logo {
    font-size: 36px;
    color: #fff;
    font-family: sans-serif;
    margin-left: 78px;
}
.inputBar {
    margin-left: 225px;
    position: relative;
    .fa-search {
        margin-left: 10px;
        position: absolute;
        color: #fff;
        font-size: 20px;
    }
    input[type="text"] {
        width: 400px;
        border: 0;
        border-bottom: 1px solid #fff;
        background-color: #7828B4;
        font-family: sans-serif;
        font-size: 20px;

        &::placeholder {
            color: rgba(255,255,255,0.5);
            padding: 40px;
        }
    }
}
</style>
