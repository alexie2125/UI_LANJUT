
<script setup>
defineProps({
  modelValue: {
    type: String,
    default: '',
  },
})

defineEmits(['update:modelValue'])
</script>

<template>
  <div class="search-bar">
    <span class="search-icon">⌕</span>

    <input
      type="text"
      :value="modelValue"
      placeholder="Search events by name or description..."
      aria-label="Search events"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>

<style scoped>
.search-bar {
  display: flex;
  align-items: center;
  gap: 12px;
  width: 100%;
  box-sizing: border-box;
  padding: 12px 16px;
  margin-bottom: var(--space-6);
  background: #ffffff;
  border: 1px solid var(--border-color);
  border-radius: 10px;
  transition: border-color 0.2s ease;
}

.search-bar:focus-within {
  border-color: var(--primary);
}

.search-icon {
  color: var(--text-muted);
  font-size: 24px;
  line-height: 1;
}

.search-bar input {
  flex: 1;
  min-width: 0;
  border: none;
  outline: none;
  background: transparent;
  color: var(--text-main);
  font-family: inherit;
  font-size: 1rem;
}

.search-bar input::placeholder {
  color: var(--text-muted);
}
</style>
