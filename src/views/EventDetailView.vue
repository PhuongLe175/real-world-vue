<script setup>
import  {ref, onMounted} from "vue";
import EventService from "@/Event/EventService";
const event = ref(null)
const props=  defineProps({
  id:{
    required: true,
  }
})
onMounted(() => {
  EventService.getEvent(props.id)
      .then(response =>{
        event.value = response.data
      }).catch(error => {
        console.log(error)
  })
})
</script>

<template>
<div v-if="event" class="eventDetail">
  <h1>{{ event.title}}</h1>
  <p>{{ event.title}} on {{event.date}} @ {{event.location}}</p>
  <p>{{ event.description}}</p>
</div>
</template>

<style scoped>
.eventDetail{
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>