<script lang="ts">
import { defineComponent, PropType } from 'vue';

export default defineComponent({
  name: 'Button',
  props: {
    type: {
      type: String as PropType<'button' | 'submit' | 'reset'>,
      default: 'button',
    },
    onClick: {
      type: Function as PropType<() => void>,
      default: () => null,
    },
    loading: {
      type: Boolean as PropType<boolean>,
      default: false,
    },
  },
  emits: ['click'],
});
</script>

<template>
  <button
    :type="type"
    class="bg-pokemon-red text-white px-4 py-2 rounded border-4 border-black"
    @click="$emit('click')"
  >
    <span v-if="loading">Loading...</span>
    <span v-else><slot /></span>
  </button>
</template>
