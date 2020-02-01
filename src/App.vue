<template>
  <div id="app">
    <div class="header-area">
      <div class="container">
        <div class="header">
          <h2>Vue-Calculator</h2>
        </div>
      </div>
    </div>

    <div class="container">
      <div class="calculator">
        <Calculator />
      </div>
    </div>
  </div>
</template>

<script>
import Calculator from "@/components/Calculator";
export default {
  components: {
    Calculator
  }
};
</script>
<style lang="scss">
@import "~bootstrap/dist/css/bootstrap.min";
.header-area {
  background-color: #6c5ce7;
  padding: 100px 0;
  .header {
    h2 {
      color: #fff;
    }
  }
}
</style>
