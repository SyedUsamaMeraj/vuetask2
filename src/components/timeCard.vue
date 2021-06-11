<template>
  <div id="timeCard">
    <b-card tag="article" style="max-width: 40rem" class="mb-2">
      <b-card-text
        ><h4>{{ dayName }}</h4></b-card-text
      >
      <div class="time-row">
        <div class="time-checkbox">
          <select
            v-model="addTime.startTime"
            class="m-md-2 select"
            id="startTime"
            required
          >
            <option v-for="time in timeList" :key="time.id" :value="time.value">
              {{ time.label }}
            </option>
          </select>
          <select
            v-model="addTime.endTime"
            class="m-md-2 select"
            id="endTime"
            :class="{ disabled: selectDisabled }"
            :disabled="selectDisabled"
            required
          >
            <option v-for="time in timeList" :key="time.id" :value="time.value">
              {{ time.label }}
            </option>
          </select>
        </div>

        <div class="mt-2 mb-3 btn-row">
          <b-button
            variant="success"
            @click="submitTime()"
            :class="{ disabled: buttonDisabled }"
            :disabled="buttonDisabled"
            >Add Time</b-button
          >
        </div>
      </div>
      <div class="mt-2 time-list">
        <div class="alert-msg">
          <b-alert
            :variant="sameTime ? 'danger' : 'warning'"
            show
            dismissible
            v-if="errorMessage"
          >
            {{ errorMessage }}
          </b-alert>
        </div>
        <ul>
          <li v-for="time in sortTime(times)" :key="time.id">
            <h2>
              {{
                `${convertTime(time.startTime)} - ${convertTime(time.endTime)}`
              }}
            </h2>
            <button @click="deleteTime(index)">X</button>
          </li>
        </ul>
      </div>
    </b-card>
  </div>
</template>

<script>
export default {
  props: {
    dayName: {
      required: true,
    },
  },
  data() {
    return {
      addTime: {
        startTime: { value: "" },
        endTime: { value: "" },
      },
      times: [],
      errorMessage: "",
      invalidTime: false,
      sameTime: false,
      timeList: [
        { value: null, label: "Choose A Time" },
        { value: 0, label: "12:00 AM" },
        { value: 1, label: "01:00 AM" },
        { value: 2, label: "02:00 AM" },
        { value: 3, label: "03:00 AM" },
        { value: 4, label: "04:00 AM" },
        { value: 5, label: "05:00 AM" },
        { value: 6, label: "06:00 AM" },
        { value: 7, label: "07:00 AM" },
        { value: 8, label: "08:00 AM" },
        { value: 9, label: "09:00 AM" },
        { value: 10, label: "10:00 AM" },
        { value: 11, label: "11:00 AM" },
        { value: 12, label: "12:00 PM" },
        { value: 13, label: "01:00 PM" },
        { value: 14, label: "02:00 PM" },
        { value: 15, label: "03:00 PM" },
        { value: 16, label: "04:00 PM" },
        { value: 17, label: "05:00 PM" },
        { value: 18, label: "06:00 PM" },
        { value: 19, label: "07:00 PM" },
        { value: 20, label: "08:00 PM" },
        { value: 21, label: "09:00 PM" },
        { value: 22, label: "10:00 PM" },
        { value: 23, label: "11:00 PM" },
      ],
    };
  },
  methods: {
    sortTime: function (time) {
      return time.slice().sort(function (a, b) {
        if (a.startTime < b.startTime) {
          return -1;
        } else if (a.sameTime > b.sameTime) {
          return 1;
        } else if (a.endTime < b.endTime) {
          return -1;
        } else if (a.endTime > b.endTime) {
          return 1;
        } else {
          return 0;
        }
      });
    },
    convertTime(time) {
      let addedTime = time;
      let prefix = "AM";
      let hours = addedTime;
      if (hours >= 12) {
        hours = addedTime - 12;
        prefix = "PM";
      }
      if (hours == 0) {
        hours = 12;
      }
      let Datetime = hours + ": 00 " + prefix;
      return Datetime;
    },
    checkForExistance() {
      return this.times.find(
        (item) =>
          item.startTime === this.addTime.startTime &&
          item.endTime === this.addTime.endTime
      );
    },
    submitTime() {
      if (this.checkForExistance() !== undefined) {
        this.errorMessage = "Time Already Exists";
        this.sameTime = true;
        this.invalidTime = false;
      } else if (
        this.addTime.startTime > this.addTime.endTime ||
        this.addTime.startTime === this.addTime.endTime ||
        this.addTime.startTime === null ||
        this.addTime.endTime === null
      ) {
        this.errorMessage = "Invalid Time Selected";
        this.invalidTime = true;
        this.sameTime = false;
      } else {
        this.times.push({
          startTime: this.addTime.startTime,
          endTime: this.addTime.endTime,
        });
        this.errorMessage = "";
        this.invalidTime = false;
        this.sameTime = false;
      }
    },
    deleteTime(index) {
      this.times.splice(index, 1);
    },
  },
  computed: {
    selectDisabled() {
      if (
        this.addTime.startTime !== null &&
        this.addTime.startTime.value !== ""
      ) {
        return false;
      } else {
        return true;
      }
    },
    buttonDisabled() {
      if (
        this.addTime.startTime !== null &&
        this.addTime.endTime !== null &&
        this.addTime.startTime.value !== "" &&
        this.addTime.endTime.value !== ""
      ) {
        return false;
      } else {
        return true;
      }
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
select:disabled {
  pointer-events: none;
}
.disabled select {
  pointer-events: none;
}
</style>
