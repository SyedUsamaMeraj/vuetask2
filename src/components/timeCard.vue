<template>
  <div id="timeCard">
    <b-card tag="article" style="max-width: 40rem" class="mb-2">
      <b-card-text> </b-card-text>
      <div class="time-row">
        <div class="time-checkbox">
          <select
            v-model="startTime"
            class="m-md-2 select"
            id="startTime"
            required
          >
            <option selected disabled>Choose a time</option>
            <option value=""></option>
            <option>00:00</option>
            <option>01:00</option>
            <option>02:00</option>
            <option>03:00</option>
            <option>04:00</option>
            <option>05:00</option>
            <option>06:00</option>
            <option>07:00</option>
            <option>08:00</option>
            <option>09:00</option>
            <option>10:00</option>
            <option>11:00</option>
            <option>12:00</option>
            <option>13:00</option>
            <option>14:00</option>
            <option>15:00</option>
            <option>16:00</option>
            <option>17:00</option>
            <option>18:00</option>
            <option>19:00</option>
            <option>20:00</option>
            <option>21:00</option>
            <option>22:00</option>
            <option>23:00</option>
          </select>
          <select
            v-model="endTime"
            class="m-md-2 select"
            id="endTime"
            :class="{ disabled: selectDisabled }"
            :disabled="selectDisabled"
            required
          >
            <option selected disabled>Choose a time</option>
            <option value=""></option>
            <option>00:00</option>
            <option>01:00</option>
            <option>02:00</option>
            <option>03:00</option>
            <option>04:00</option>
            <option>05:00</option>
            <option>06:00</option>
            <option>07:00</option>
            <option>08:00</option>
            <option>09:00</option>
            <option>10:00</option>
            <option>11:00</option>
            <option>12:00</option>
            <option>13:00</option>
            <option>14:00</option>
            <option>15:00</option>
            <option>16:00</option>
            <option>17:00</option>
            <option>18:00</option>
            <option>19:00</option>
            <option>20:00</option>
            <option>21:00</option>
            <option>22:00</option>
            <option>23:00</option>
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
          <b-alert show dismissible v-if="msg">
            {{ msg }}
          </b-alert>
        </div>
        <div class="alert-msg">
          <b-alert variant="warning" show dismissible v-if="invalidTime">
            {{ invalidTime }}
          </b-alert>
        </div>
        <ul>
          <li v-for="(time, index) in times" :key="time.id">
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
  data() {
    return {
      startTime: "",
      endTime: "",
      times: [],
      msg: "",
      invalidTime: "",
    };
  },
  methods: {
    submitTime() {
      if (this.times.includes(this.startTime + " - " + this.endTime)) {
        this.msg = "Time Already Exists";
        this.invalidTime = "";
      } else if (
        this.startTime > this.endTime ||
        this.startTime == this.endTime
      ) {
        this.invalidTime = "Invalid Time Selected";
        this.msg = "";
      } else {
        this.times.push(this.startTime + " - " + this.endTime);
        this.msg = "";
        this.invalidTime = "";
      }
    },
    deleteTime(index) {
      this.times.splice(index, 1);
    },
  },
  computed: {
    selectDisabled() {
      if (this.startTime.length > 1) {
        return false;
      } else {
        return true;
      }
    },
    buttonDisabled() {
      if (this.startTime.length > 1 && this.endTime.length > 1) {
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
.asc:after {
  content: "\25B2";
}

.desc:after {
  content: "\25BC";
}
</style>
