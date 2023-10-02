<template>
  <div
    class="multiselect-detail-field-value relative o1-rounded border bg-white o1-border-gray-200 dark:o1-bg-gray-900 dark:o1-border-gray-700"
    v-if="values"
  >
    <div v-if="field.belongsToManyResourceName && field.viewable" class="overflow-hidden">
      <div v-for="(option, i) of values" :key="i" class="multiselect-detail-row border-b o1-border-gray-200 dark:o1-border-slate-800 o1-text-sm hover:o1-bg-slate-50 dark:hover:o1-bg-gray-800">
        <Link
          class="link-default block o1-py-1 o1-px-2"
          :href="$url(`/resources/${field.belongsToManyResourceName}/${field.value[i]}`)"
        >
          {{ option }}
        </Link>
      </div>
    </div>
    <div v-else class="overflow-hidden">
      <div
        class="multiselect-detail-row border-b o1-border-gray-200 dark:o1-border-slate-800 o1-text-sm o1-py-1 o1-px-2 hover:o1-bg-slate-50 dark:hover:o1-bg-gray-800"
        v-for="(value, i) of values"
        :key="i"
      >
        <div v-if="field?.isColorful && isColor(value)" style="display: flex; align-items: center;">
          <div :style="{ backgroundColor: value, width: '20px', height: '20px', marginRight: '5px' }"></div>
          <span>{{ value }}</span>
        </div>
        <span v-else>{{ value }}</span>

      </div>
    </div>
  </div>

  <div v-else>—</div>
</template>

<script>
export default {
  props: ['field', 'values'],

  methods: {
    isColor(strColor) {
      const colorPattern = /^#([0-9a-f]{3}){1,2}$/i;
      return colorPattern.test(strColor);
    },
  }
};
</script>

<style lang="scss" scoped>
.multiselect-detail-field-value {
  .multiselect-detail-row {
    &:last-child {
      border-bottom: none;
    }
  }
}
</style>
