
<script setup>
defineProps({
  variant: {
    type: String,
    default: 'primary'
  }
})
</script>

<template>
  <button :class="['app-button', `btn-${variant}`]">
    <slot />
  </button>
</template>

<style scoped>
.app-button {
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.btn-primary {
  background-color: #4f46e5;
  color: #ffffff;
}

.btn-primary:hover {
  background-color: #4338ca;
}

.btn-secondary {
  background-color: #f3f4f6;
  color: #374151;
}

.btn-secondary:hover {
  background-color: #e5e7eb;
}
</style>
