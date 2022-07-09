<template>
  <div class="table">
    <div class="table-header">studying</div>
    <div class="wrapper">
      <TrackerNumber
        v-for="(number, index) in numbersArray"
        :key="index"
        :number="number.number"
        :selected="number.selected"
        @selected="onSelected(index)"
      />
      <div class="sum">
        {{ `${selectedNumbersLength}/${numbersArray.length}` }}
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, computed, ref } from "@vue/runtime-core";
import TrackerNumber from "./TrackerNumber.vue";
import { Item } from "@/types/Item";

export default defineComponent({
  name: "HabbitTracker",
  components: {
    TrackerNumber,
  },
  props: {
    monthsLength: {
      type: Number,
      default: 31,
    },
  },
  setup(props) {
    const numbersArray = ref<Item[]>(
      Array.from(Array(props.monthsLength)).map((_, index) => ({
        number: index + 1,
        selected: false,
      }))
    );

    const selectedNumbersLength = computed(
      () => numbersArray.value.filter(({ selected }) => selected).length
    );

    const onSelected = (index: number) => {
      numbersArray.value[index].selected = !numbersArray.value[index].selected;
    };

    return {
      numbersArray,
      selectedNumbersLength,
      onSelected,
    };
  },
});
</script>

<style lang="scss" scoped>
.table {
  margin-left: 200px;
  margin-top: 200px;
  width: 214px;
  height: 182px;
  border: 2px solid var(--pink);

  &-header {
    width: 212px;
    height: 30px;
    background-color: var(--pink);
    color: var(--white);
    font-weight: 600;
    line-height: 30px;
    text-transform: uppercase;
    font-size: 0.9rem;
  }
}
.wrapper {
  display: flex;
  flex-wrap: wrap;
}
.sum {
  text-align: center;
  line-height: 30px;
  font-weight: 500;
  margin: 0 auto;
}
</style>
