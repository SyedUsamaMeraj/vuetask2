<template>
  <div id="daysList">
    <div class="mb-5 checkboxes">
      <ul>
        <li v-for="day in daylist" v-bind:key="day.id">
          <b-form-checkbox size="lg" v-bind:value="day" v-model="days">{{
            day
          }}</b-form-checkbox>
        </li>
      </ul>
    </div>

    <div class="cardsList flex">
      <div
        class="cards"
        v-for="selectedDay in days"
        v-bind:key="selectedDay.id"
      >
        <h4>{{ selectedDay }}</h4>
        <time-card></time-card>
      </div>
    </div>
  </div>
</template>

<script>
import timeCard from "./timeCard.vue";
export default {
  components: { "time-card": timeCard },
  data() {
    return {
      timeCard: undefined,
      days: [],
      selectedDay: "",
      startTime: "",
      endTime: "",
      daylist: [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ],
    };
  },
};
</script>

<style scoped>
.checkboxes {
  display: flex;
  justify-content: space-evenly;
  border: 1px solid #000;
}
.checkboxes ul li {
  display: inline-block;
  margin-right: 30px;
}
.checkbox {
  display: flex;
  flex-direction: column;
  padding: 10px;
  margin-right: 10px;
  text-align: center;
}

.flex {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>
