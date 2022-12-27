<template>
  <div class="text-center">
    <p>Selam Vue , {{ content }}</p>
    <slot></slot>
    <slot name="NamedSlot"></slot>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  //Prop alırken aşağıdaki kullanıma özen göster props propertysi içine bir array alır ve her prop arrayin bir elementidir !!
  props: ["content"],
};
</script>
<style scoped>
div {
  border: 1px solid #ccc;
  box-shadow: 1px 1px 2px #666;
  padding: 20px 20px;
  margin-top: 20px;
}
</style>
