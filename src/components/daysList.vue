<template>
  <div id="daysList">
    <div class="mb-5 checkbox-container">
      <ul>
        <li v-for="day in daylist" :key="day.id" class="mt-3">
          <b-form-checkbox size="lg" :value="day" v-model="selectedDays">{{
            day.name
          }}</b-form-checkbox>
        </li>
      </ul>
    </div>

    <div class="flex cardsList">
      <div class="cards" v-for="day in sortDay(selectedDays)" :key="day.name">
        <time-card :dayName="day.name"></time-card>
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
      daylist: [
        { value: 1, name: "Sunday" },
        { value: 2, name: "Monday" },
        { value: 3, name: "Tuesday" },
        { value: 4, name: "Wednesday" },
        { value: 5, name: "Thursday" },
        { value: 6, name: "Friday" },
        { value: 7, name: "Saturday" },
      ],
    };
  },
  methods: {
    sortDay: function (day) {
      return day.slice().sort(function (a, b) {
        return a.value - b.value;
      });
    },
    addDays() {
      this.selectedDays.push(
        { value: this.daylist.value },
        { name: this.daylist.name }
      );
    },
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
