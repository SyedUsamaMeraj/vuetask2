<template>
  <div id="timeCard">
    <b-card tag="article" style="max-width: 40rem" class="mb-2">
      <b-card-text>
        {{ selectedDay }}
      </b-card-text>
      <div class="time-row">
        <div class="time-checkbox">
          <select v-model="startTime" class="m-md-2 select" id="dropdown-1">
            <option selected disabled>Choose a time</option>
            <option>12:00 AM</option>
            <option>01:00 AM</option>
            <option>02:00 AM</option>
            <option>03:00 AM</option>
            <option>04:00 AM</option>
            <option>05:00 AM</option>
            <option>06:00 AM</option>
            <option>07:00 AM</option>
            <option>08:00 AM</option>
            <option>09:00 AM</option>
            <option>10:00 AM</option>
            <option>11:00 AM</option>
            <option>12:00 PM</option>
            <option>01:00 PM</option>
            <option>02:00 PM</option>
            <option>03:00 PM</option>
            <option>04:00 PM</option>
            <option>05:00 PM</option>
            <option>06:00 PM</option>
            <option>07:00 PM</option>
            <option>08:00 PM</option>
            <option>09:00 PM</option>
            <option>10:00 PM</option>
            <option>11:00 PM</option>
          </select>
          <select v-model="endTime" class="m-md-2 select" id="dropdown-1">
            <option selected disabled>Choose a time</option>
            <option>12:00 AM</option>
            <option>01:00 AM</option>
            <option>02:00 AM</option>
            <option>03:00 AM</option>
            <option>04:00 AM</option>
            <option>05:00 AM</option>
            <option>06:00 AM</option>
            <option>07:00 AM</option>
            <option>08:00 AM</option>
            <option>09:00 AM</option>
            <option>10:00 AM</option>
            <option>11:00 AM</option>
            <option>12:00 PM</option>
            <option>01:00 PM</option>
            <option>02:00 PM</option>
            <option>03:00 PM</option>
            <option>04:00 PM</option>
            <option>05:00 PM</option>
            <option>06:00 PM</option>
            <option>07:00 PM</option>
            <option>08:00 PM</option>
            <option>09:00 PM</option>
            <option>10:00 PM</option>
            <option>11:00 PM</option>
          </select>
        </div>

        <div class="mb-5 btn-row">
          <b-button variant="success" @click="submitTime">Add Time</b-button>
        </div>
      </div>
      <div class="time-list">
        <ul>
          <li v-for="(time, index) in times" v-bind:key="time.id">
            <h5>{{ time }}</h5>

            <button @click="deleteTime(index)">X</button>
          </li>
        </ul>
      </div>
    </b-card>
  </div>
</template>

<script>
export default {
  props: ["selectedDay"],
  data() {
    return {
      startTime: "",
      endTime: "",
      times: [],
    };
  },
  methods: {
    submitTime() {
      this.times.push(this.startTime + " - " + this.endTime);
    },
    deleteTime(index) {
      this.times.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.time-row {
  padding: 10px 15px;
  background: rgb(224, 224, 224);
}
.btn-row {
  text-align: right;
}
.time-checkbox {
  display: flex;
  justify-content: space-evenly;
}
.time-list ul li {
  width: 100%;
  display: flex;
}
.time-list ul li button {
  background: transparent;
  border: none;
  width: auto;
  margin-left: auto;
}
select {
  outline: 0;
  box-shadow: none;
  border: 0 !important;
  background: #2c3e50;
  background-image: none;
  position: relative;
  display: flex;
  width: 20em;
  height: 3rem;
  line-height: 3;
  background: #2c3e50;
  overflow: hidden;
  border-radius: 0.25em;

  flex: 1;
  padding: 0 0.5em;
  color: #fff;
  cursor: pointer;
}
/* Arrow */
.select::after {
  content: "\25BC";
  position: absolute;
  top: 0;
  right: 0;
  padding: 0 1em;
  background: #34495e;
  cursor: pointer;
  pointer-events: none;
  -webkit-transition: 0.25s all ease;
  -o-transition: 0.25s all ease;
  transition: 0.25s all ease;
}
/* Transition */
.select:hover::after {
  color: #f39c12;
}
.cardsList {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.time-list ul {
  width: 100%;
}
</style>
