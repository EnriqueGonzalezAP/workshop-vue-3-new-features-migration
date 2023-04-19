<template>
  <label class="font-bold mb-2 flex">{{ label }}</label>
  <ul v-bind="$attrs">
    <li v-for="option in options" @click="toggleElement(option)" class="cursor-pointer">
      {{ option }}
      <span v-if="this.selectedItems.find(o => o.option === option).selected">✅</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: ['modelValue', 'label', 'options'],
  data() {
    return {
      selectedItems: this.options.map(o => {
        return {
          option: o,
          selected: this.modelValue.includes(o)
        }
      })
    }
  },
  methods: {
    toggleElement(option) {
      let item = this.selectedItems.find(o => o.option === option);
      item.selected = !item.selected
      this.$emit('update:modelValue', this.selectedItems.filter(o => o.selected).map(o => o.option));
    }
  }
}
</script>