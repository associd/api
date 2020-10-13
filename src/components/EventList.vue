<template>
  <div class="event-list">
    <h2 class="bg-dark text-white">EventList</h2>
    <div id="list-group">
      <router-link :to="'eventAgenda/' + event.organizer.slug + '/' + event.slug" class="event list-group-item" v-for="event in events" :key="event.id">
        <h4>
          {{ event.name}}
        </h4>
        <div>
          {{event.organizer.name}}
          {{ event.slug}}
          <div class="float-right">
            {{event.date}}
          </div>
        </div>
      </router-link>
    </div>
  </div>

</template>

<script>
export default {
  data: function () {
    return {
      events: []
    }
  },
  created() {
    fetch("http://localhost/day2-afternoon/api/v1/events")
        .then(res => {
          res.json()
              .then(data =>{
                this.events = data.events
              })
        })
  }
}
</script>

<style>

h2{
  padding: 15px;
}
#list-group .event:hover{
  background-color: #343a40;
  color: white;
}
.list-group-item{
  margin: 15px;
  box-shadow: 2px 2px 4px gray;
  color: #343a40;
}

</style>