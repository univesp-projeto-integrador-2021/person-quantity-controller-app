<template>
  <div>
    <button class="btn">{{ buttonName }}</button>
  </div>
</template>

<script>
export default {
  props: ["buttonName"],
};
</script>

<style>
.btn {
  height: 37px;
  padding: 0 20px;
  border-radius: 6px;
  background-color: #fc8a4a;
  color: #fff;
  font-weight: 700;
  cursor: pointer;
}
</style>
