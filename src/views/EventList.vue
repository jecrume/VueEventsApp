<template>
  <h1>Events For Good</h1>
  <div class="events">
    
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import EventService from '@/services/EventService.js'

export default {
  name: "EventList",
  components: {
    EventCard
  },
  data(){
    return{
      events:null
    }
  },
  created (){

      //Get the events data
      EventService.getEvents()
      //wait for the response and save events to the events list
      .then(response => {this.events = response.data})
      //catch any errors
      .catch(error =>{ console.log(error)})

    }
    
};
</script>

<style scoped>
  .events{
    display:flex;
    flex-direction: column;
    align-items: center;
    }
</style>
