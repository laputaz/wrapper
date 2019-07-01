<template>
  <div class="dh-page">
    <Wrapper :option="option" />
  </div>
</template>
<script>
import Wrapper from "../components/Wrapper.vue";
import option from "./option.js"
export default {
  components: {
    Wrapper
  },
  created(){
    this.option = option
  }
};
</script>
<style lang="less" scoped>
.dh-page {
  background-color: burlywood;
  padding: 50px;
}
</style>
