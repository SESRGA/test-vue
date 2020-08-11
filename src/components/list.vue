<template>
  <div>
    <item
      v-for="elem in elems" :key ="elem"
      @change-elem="changeColor"
      :class="{ active: elem.active }"
      v-bind:elem="elem"
    />
  </div>
</template>

<script>
import item from "@/components/item";
export default {
  props: ['elems'],
  name: "list",
  components: {
    item
  },
  methods: {
    changeColor(el) {
      this.$emit('change-elem', el)
    }
  }
}

</script>

<style scoped>
.active {
  color: white;
  background: red;
}
</style>
