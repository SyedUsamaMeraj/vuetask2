<template>
  <div id="daysList">
    <div class="mb-5 checkbox-container">
      <ul>
        <li v-for="day in daylist" :key="day.id" class="mt-3" :day="day">
          <b-form-checkbox size="lg" :value="day" v-model="selectedDays">{{
            day.name
          }}</b-form-checkbox>
        </li>
      </ul>
    </div>

    <div class="flex cardsList">
      <div class="cards" v-for="day in selectedDays" :key="day.id">
        <h4>
          {{ day.name }}
        </h4>
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
        { index: 1, name: "Sunday" },
        { index: 2, name: "Monday" },
        { index: 3, name: "Tuesday" },
        { index: 4, name: "Wednesday" },
        { index: 5, name: "Thursday" },
        { index: 6, name: "Friday" },
        { index: 7, name: "Saturday" },
      ],
    };
  },
  methods: {
    addDays() {
      this.selectedDays.push(
        { index: this.daylist.index },
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
