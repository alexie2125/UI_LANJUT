
<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'

import EventCard from '../components/event/EventCard.vue'
import SearchBar from '../components/event/SearchBar.vue'
import CategoryFilter from '../components/event/CategoryFilter.vue'

const router = useRouter()

const events = [
  {
    id: 1,
    title: 'Vue.js Mastery Workshop',
    date: 'Oct 12, 2026',
    loc: '📍 Tech Hub, Jakarta',
    cat: 'Workshop',
    desc: 'Learn advanced Vue 3 concepts, Composition API, and state management to build high-performance web applications interactively.',
  },
  {
    id: 2,
    title: 'National Tech Meetup',
    date: 'Oct 15, 2026',
    loc: '📍 Main Auditorium, City Center',
    cat: 'Meetup',
    desc: 'A gathering of hundreds of developers and tech enthusiasts to share the latest industry trends and expand professional networks.',
  },
  {
    id: 3,
    title: 'Startup Pitch Competition',
    date: 'Nov 02, 2026',
    loc: '📍 Innovation Center',
    cat: 'Competition',
    desc: 'Watch the best local startup founders pitch their innovative ideas live in front of a panel of renowned investors.',
  },
  {
    id: 4,
    title: 'UI/UX Design Sprint',
    date: 'Nov 10, 2026',
    loc: '📍 Creative Studio',
    cat: 'Workshop',
    desc: 'A hands-on session on designing user interfaces by implementing layout systems and visual hierarchy principles.',
  },
  {
    id: 5,
    title: 'Digital Marketing Seminar',
    date: 'Nov 20, 2026',
    loc: '📍 Grand Hotel Hall',
    cat: 'Seminar',
    desc: 'An in-depth seminar dissecting modern digital marketing strategies, from SEO optimization to user conversion tactics.',
  },
  {
    id: 6,
    title: 'Community Leaders Summit',
    date: 'Dec 05, 2026',
    loc: '📍 Gatherly HQ',
    cat: 'Conference',
    desc: 'An exclusive year-end conference for community leaders to formulate sustainable ecosystem development strategies.',
  },
]

const searchQuery = ref('')
const selectedCategory = ref('All')

const categories = computed(() => [
  'All',
  ...new Set(events.map((event) => event.cat)),
])

const filteredEvents = computed(() => {
  const keyword = searchQuery.value.trim().toLowerCase()

  return events.filter((event) => {
    const matchesCategory =
      selectedCategory.value === 'All' ||
      event.cat === selectedCategory.value

    const searchableText = [
      event.title,
      event.desc,
      event.date,
      event.loc,
      event.cat,
    ]
      .join(' ')
      .toLowerCase()

    const matchesSearch = searchableText.includes(keyword)

    return matchesCategory && matchesSearch
  })
})

function handleViewDetail(eventId) {
  router.push(`/browse/events/${eventId}`)
}
</script>

<template>
  <div class="event-list-page">
    <div class="header-section">
      <h2 class="section-title">Upcoming Events</h2>
      <p class="section-desc">
        Discover workshops, seminars, tech meetups, and competitions near you.
      </p>
    </div>

    <SearchBar v-model="searchQuery" />

    <CategoryFilter
      v-model="selectedCategory"
      :categories="categories"
    />

    <div v-if="filteredEvents.length > 0" class="event-grid">
      <EventCard
        v-for="event in filteredEvents"
        :key="event.id"
        :event="event"
        @view-detail="handleViewDetail"
      />
    </div>

    <div v-else class="empty-state">
      <h3>No events found</h3>
      <p>
        No events match your search. Try another keyword or category.
      </p>
    </div>
  </div>
</template>

<style scoped>
.event-list-page {
  width: 100%;
}

.header-section {
  margin-bottom: var(--space-8);
}

.section-title {
  font-size: 2.2rem;
  margin-bottom: var(--space-2);
}

.section-desc {
  color: var(--text-muted);
  font-size: 1.1rem;
}

.event-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: var(--space-6);
  align-items: stretch;
}

.empty-state {
  padding: 40px 24px;
  border: 1px dashed var(--border-color);
  border-radius: 12px;
  text-align: center;
  color: var(--text-muted);
  background: #ffffff;
}

.empty-state h3 {
  color: var(--text-main);
  margin-bottom: var(--space-2);
}

.empty-state p {
  line-height: 1.6;
}
</style>
