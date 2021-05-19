<template>
  <div id="datatimecard">
    <div class="card w-50">
      <h3>Sunday</h3>
      <div class="time-row">
        <b-dropdown id="dropdown-1" text="Start Time" class="m-md-2">
          <b-dropdown-item>12:00 AM</b-dropdown-item>
          <b-dropdown-item>01:00 AM</b-dropdown-item>
          <b-dropdown-item>02:00 AM</b-dropdown-item>
          <b-dropdown-item>03:00 AM</b-dropdown-item>
          <b-dropdown-item>04:00 AM</b-dropdown-item>
          <b-dropdown-item>05:00 AM</b-dropdown-item>
          <b-dropdown-item>06:00 AM</b-dropdown-item>
          <b-dropdown-item>07:00 AM</b-dropdown-item>
          <b-dropdown-item>08:00 AM</b-dropdown-item>
          <b-dropdown-item>09:00 AM</b-dropdown-item>
          <b-dropdown-item>10:00 AM</b-dropdown-item>
          <b-dropdown-item>11:00 AM</b-dropdown-item>
          <b-dropdown-item>12:00 PM</b-dropdown-item>
          <b-dropdown-item>01:00 PM</b-dropdown-item>
          <b-dropdown-item>02:00 PM</b-dropdown-item>
          <b-dropdown-item>03:00 PM</b-dropdown-item>
          <b-dropdown-item>04:00 PM</b-dropdown-item>
          <b-dropdown-item>05:00 PM</b-dropdown-item>
          <b-dropdown-item>06:00 PM</b-dropdown-item>
          <b-dropdown-item>07:00 PM</b-dropdown-item>
          <b-dropdown-item>08:00 PM</b-dropdown-item>
          <b-dropdown-item>09:00 PM</b-dropdown-item>
          <b-dropdown-item>10:00 PM</b-dropdown-item>
          <b-dropdown-item>11:00 PM</b-dropdown-item>
        </b-dropdown>
        <b-dropdown id="dropdown-1" text="End Time" class="m-md-2">
          <b-dropdown-item>12:00 AM</b-dropdown-item>
          <b-dropdown-item>01:00 AM</b-dropdown-item>
          <b-dropdown-item>02:00 AM</b-dropdown-item>
          <b-dropdown-item>03:00 AM</b-dropdown-item>
          <b-dropdown-item>04:00 AM</b-dropdown-item>
          <b-dropdown-item>05:00 AM</b-dropdown-item>
          <b-dropdown-item>06:00 AM</b-dropdown-item>
          <b-dropdown-item>07:00 AM</b-dropdown-item>
          <b-dropdown-item>08:00 AM</b-dropdown-item>
          <b-dropdown-item>09:00 AM</b-dropdown-item>
          <b-dropdown-item>10:00 AM</b-dropdown-item>
          <b-dropdown-item>11:00 AM</b-dropdown-item>
          <b-dropdown-item>12:00 PM</b-dropdown-item>
          <b-dropdown-item>01:00 PM</b-dropdown-item>
          <b-dropdown-item>02:00 PM</b-dropdown-item>
          <b-dropdown-item>03:00 PM</b-dropdown-item>
          <b-dropdown-item>04:00 PM</b-dropdown-item>
          <b-dropdown-item>05:00 PM</b-dropdown-item>
          <b-dropdown-item>06:00 PM</b-dropdown-item>
          <b-dropdown-item>07:00 PM</b-dropdown-item>
          <b-dropdown-item>08:00 PM</b-dropdown-item>
          <b-dropdown-item>09:00 PM</b-dropdown-item>
          <b-dropdown-item>10:00 PM</b-dropdown-item>
          <b-dropdown-item>11:00 PM</b-dropdown-item>
        </b-dropdown>
        <div class="btn-row">
          <b-button variant="success">Add Time</b-button>
        </div>
        <div class="time-list">
          <ul>
            <li v-for="(time, index) in times" v-bind:key="time.id">
              {{ time }}

              <button @click="deleteTime(index)">X</button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
</script>

<style scoped>
#datatimecard {
  border-radius: 5px;
  border: 2px solid #000;
  box-shadow: 0px 0px 5px #000;
}
.time-row {
  padding: 10px 15px;
}
.btn-row {
  text-align: right;
}
</style>
