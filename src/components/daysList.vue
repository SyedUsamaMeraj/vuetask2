<template>
  <div id="daysList">
    <div class="mb-5 checkbox-container">
      <ul>
        <li v-for="day in daylist" :key="day.id" class="mt-3">
          <b-form-checkbox size="lg" :value="day" v-model="selectedDays">{{
            day
          }}</b-form-checkbox>
        </li>
      </ul>
    </div>

    <div class="cardsList flex">
      <div class="cards" v-for="day in selectedDays" :key="day.id">
        <h4>{{ day }}</h4>
        <time-card></time-card>
      </div>
    </div>
  </div>
</template>

<script>
import timeCard from "./timeCard.vue";
export default {
  components: { timeCard },
  data() {
    return {
      selectedDays: [],
      day: "",
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
.checkbox-container {
  display: flex;
  justify-content: space-evenly;
  border: 1px solid #000;
}
.checkbox-container ul li {
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
