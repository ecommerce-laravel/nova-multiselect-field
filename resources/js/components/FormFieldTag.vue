<template>
  <span class="multiselect__tag">
    <div v-if="field?.isColorful && isColor(option.label)" style="display: flex; align-items: center;">
      <div :style="{ backgroundColor: option.label, width: '20px', height: '20px', marginRight: '5px' }"></div>
      <span>{{ option.label }}</span>
    </div>
    <span v-else>{{ option.label }}</span>
    <i class="multiselect__tag-icon" @click="remove(option)"></i>
  </span>
</template>

<script>
export default {
  props: ['option', 'remove', 'field'], // ensure field is a prop
  methods: {
    isColor(strColor) {
      const colorPattern = /^#([0-9a-f]{3}){1,2}$/i;
      return colorPattern.test(strColor);
    },
  },
};
</script>