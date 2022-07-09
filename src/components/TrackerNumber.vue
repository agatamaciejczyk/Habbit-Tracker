<template>
  <div
    class="number"
    @click="$emit('selected')"
    :class="{ 'picked-number': selected }"
  >
    {{ number }}
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

export default defineComponent({
  name: "TrackerNumber",
  props: {
    number: {
      type: Number,
      default: 1,
    },
    selected: {
      type: Boolean,
      default: false,
    },
  },
});
</script>

<style lang="scss" scoped>
.number {
  width: 30px;
  height: 30px;
  border: 2px solid var(--pink);
  border-top: none;
  border-left: none;
  color: var(--pink);
  text-align: center;
  line-height: 30px;
  font-weight: 500;
  cursor: pointer;

  &:nth-of-type(7n) {
    border-right: none;
  }
}

.picked-number {
  background-color: var(--pink);
  color: var(--white);
}
</style>
