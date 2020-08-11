<template>
  <div @click="$emit('change-elem', elem)">
    {{ elem.name }}
  </div>
</template>

<script>
export default {
  props: {
    elem: {
      type: Object,
      required: true
    }
  },
name: "item",

}
</script>

<style scoped>
div {
  border: 1px solid #2c3e50;
  height: 50px;
  padding: .5rem 2rem;
  margin-bottom: 1rem;
}

</style>
