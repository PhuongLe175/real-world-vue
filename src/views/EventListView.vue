<script setup>
import  EventCard  from '@/components/EventCard.vue'
import {ref, onMounted} from "vue";
import EventService from "@/Event/EventService";

const events = ref(null)
onMounted(() =>{
  EventService.getEvents().then(response => {
    events.value = response.data
  })
  .catch(error => {
        console.log(error)
  })
})

</script>

<template>
  <div class="event">
    <h1>Events For Good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.event {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>