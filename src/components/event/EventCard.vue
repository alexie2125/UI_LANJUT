
<script setup>
import AppCard from '../ui/AppCard.vue'
import AppButton from '../ui/AppButton.vue'

defineProps({
  event: {
    type: Object,
    required: true,
  },
})

defineEmits(['view-detail'])
</script>

<template>
  <AppCard>
    <div class="event-body">
      <div class="event-meta">
        <span class="event-date">{{ event.date }}</span>
        <span class="event-category">{{ event.cat }}</span>
      </div>

      <h3 class="event-title">{{ event.title }}</h3>
      <p class="event-loc">{{ event.loc }}</p>
      <p class="event-desc">{{ event.desc }}</p>

      <div class="card-footer">
        <AppButton
          variant="primary"
          @click="$emit('view-detail', event.id)"
        >
          View Event Details →
        </AppButton>
      </div>
    </div>
  </AppCard>
</template>

<style scoped>
.event-body {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.event-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
  margin-bottom: var(--space-4);
}

.event-date {
  background: rgba(102, 68, 255, 0.1);
  color: var(--primary);
  padding: var(--space-1) var(--space-2);
  border-radius: 6px;
  font-weight: 600;
  font-size: 0.85rem;
}

.event-category {
  color: var(--text-muted);
  font-size: 0.85rem;
  font-weight: 500;
  text-transform: uppercase;
}

.event-title {
  margin-bottom: var(--space-2);
  font-size: 1.4rem;
}

.event-loc {
  color: var(--text-muted);
  font-size: 0.95rem;
  margin-bottom: var(--space-4);
}

.event-desc {
  color: var(--text-muted);
  line-height: 1.6;
  font-size: 0.95rem;
  margin-bottom: var(--space-6);
  flex-grow: 1;
}

.card-footer {
  border-top: 1px solid var(--border-color);
  padding-top: var(--space-4);
}
</style>
