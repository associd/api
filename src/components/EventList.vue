<template>
  <div class="event-list">
    <h2 class="bg-dark text-white">EventList</h2>
    <ul id="list-group">
      <a class="event list-group-item m-1" v-for="event in events" :key="event.id">
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
      </a>
    </ul>
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

<style scoped>
h2{
  padding: 15px;
}
#list-group .event:hover{
  background-color: #343a40;
  color: white;
}

</style>