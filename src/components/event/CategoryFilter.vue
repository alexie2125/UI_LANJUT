
<script setup>
defineProps({
  categories: {
    type: Array,
    required: true,
  },
  modelValue: {
    type: String,
    default: 'All',
  },
})

defineEmits(['update:modelValue'])
</script>

<template>
  <div class="category-filter">
    <button
      v-for="category in categories"
      :key="category"
      type="button"
      :class="[
        'category-button',
        { active: modelValue === category },
      ]"
      @click="$emit('update:modelValue', category)"
    >
      {{ category }}
    </button>
  </div>
</template>

<style scoped>
.category-filter {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: var(--space-6);
}

.category-button {
  padding: 9px 18px;
  border: 1px solid var(--border-color);
  border-radius: 999px;
  background: #ffffff;
  color: var(--text-muted);
  font-family: inherit;
  font-size: 0.9rem;
  font-weight: 500;
  cursor: pointer;
  transition:
    color 0.2s ease,
    background-color 0.2s ease,
    border-color 0.2s ease;
}

.category-button:hover {
  border-color: var(--primary);
  color: var(--primary);
}

.category-button.active {
  background: var(--primary);
  border-color: var(--primary);
  color: #ffffff;
}
</style>
