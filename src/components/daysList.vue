<template>
  <div id="daysList">
    <div class="mb-5 checkboxes">
      <div class="checkbox">
        <b-form-checkbox size="lg" v-model="checked"></b-form-checkbox>
        <h6>Sunday</h6>
      </div>
      <div class="checkbox">
        <b-form-checkbox size="lg"></b-form-checkbox>
        <h6>Monday</h6>
      </div>
      <div class="checkbox">
        <b-form-checkbox size="lg"></b-form-checkbox>
        <h6>Tuesday</h6>
      </div>
      <div class="checkbox">
        <b-form-checkbox size="lg"></b-form-checkbox>
        <h6>Wednesday</h6>
      </div>
      <div class="checkbox">
        <b-form-checkbox size="lg"></b-form-checkbox>
        <h6>Thursday</h6>
      </div>
      <div class="checkbox">
        <b-form-checkbox size="lg"></b-form-checkbox>
        <h6>Friday</h6>
      </div>
      <div class="checkbox">
        <b-form-checkbox size="lg"></b-form-checkbox>
        <h6>Saturday</h6>
      </div>
    </div>

    <div class="card w-50" v-if="checked">
      <h3>Sunday</h3>
      <div class="time-row">
        <select v-model="time" class="m-md-2" name="" id="dropdown-1">
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
        <select v-model="time2" class="m-md-2" name="" id="dropdown-1">
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
        <div class="btn-row">
          <b-button variant="success" @click="submitTime">Add Time</b-button>
        </div>
        <div class="time-list">
          <ul>
            <li v-for="(time, index) in times" v-bind:key="time.id">
              {{ time }} - {{ time2 }}

              <button @click="deleteTime(index)">X</button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      checked: false,
      time: "",
      time2: "",
      times: [],
    };
  },
  methods: {
    submitTime() {
      this.times.push(this.time);
    },
    deleteTime(index) {
      this.times.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.checkboxes {
  display: flex;
  justify-content: space-evenly;
  border: 1px solid #000;
}
.checkbox {
  display: flex;
  flex-direction: column;
  padding: 10px;
  margin-right: 10px;
  text-align: center;
}
.time-row {
  padding: 10px 15px;
}
.btn-row {
  text-align: right;
}
</style>
