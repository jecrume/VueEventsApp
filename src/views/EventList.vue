<template>
  <div class="events">
    <h1>Events For Good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import axios from 'axios'

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
      axios.get('http://my-json-server.typicode.com/jecrume/EventsProjectDB/events')
      //wait for the response and log events to console
      .then(response => {console.log('events:',response.data)})
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
