<template>
  <span class="multiselect__tag">
    <span v-if="!field.isColorful || !isColor(option.label)">{{ option.label }}</span>
    <div v-else :style="{ backgroundColor: option.label, width: '20px', height: '20px' }"></div>
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