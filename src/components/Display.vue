<template>
  <div>
    <display-segment v-bind:character="weeks" v-bind:description="weeksDescription"></display-segment>
    <display-segment v-bind:character="days" v-bind:description="daysDescription"></display-segment>
    <display-segment v-bind:character="hours" v-bind:description="hoursDescription"></display-segment>
    <display-segment v-bind:character="minutes" v-bind:description="minutesDescription"></display-segment>
    <display-segment v-bind:character="seconds" v-bind:description="secondsDescription"></display-segment>
  </div>
</template>

<script>
import DisplaySegment from "./DisplaySegment";
import moment from "moment";

export default {
  props: {
    dateTo: moment.moment,
  },
  data: function () {
    return {
      weeks: 0,
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
    };
  },
  created: function () {
    setInterval(
      function () {
        const now = moment();
        this.weeks = this.dateTo.diff(now, "weeks");
        this.days = this.dateTo
          .clone()
          .add(-this.weeks, "weeks")
          .diff(now, "days");

        this.hours = this.dateTo
          .clone()
          .add(-this.weeks, "weeks")
          .add(-this.days, "days")
          .diff(now, "hours");

        this.minutes = this.dateTo
          .clone()
          .add(-this.weeks, "weeks")
          .add(-this.days, "days")
          .add(-this.hours, "hours")
          .diff(now, "minutes");

        this.seconds = this.dateTo
          .clone()
          .add(-this.weeks, "weeks")
          .add(-this.days, "days")
          .add(-this.hours, "hours")
          .add(-this.minutes, "minutes")
          .diff(now, "seconds");
      }.bind(this),
      1000
    );
  },
  components: {
    DisplaySegment,
  },
  computed: {
    weeksDescription: function () {
      if (this.weeks === 1) {
        return "tydzień";
      } else if (this.weeks > 1) {
        return "tygodnie";
      } else {
        return "tygodni";
      }
    },
    daysDescription: function () {
      return this.days > 0 ? humanize(this.days, "days") : "dni";
    },
    hoursDescription: function () {
      return this.hours > 0 ? humanize(this.hours, "hours") : "godzin";
    },
    minutesDescription: function () {
      return humanize(this.minutes, "minutes", { m: 60 });
    },
    secondsDescription: function () {
      return humanize(this.seconds, "seconds", { s: 60 });
    },
  },
};

const humanize = function (value, unit, opts = {}) {
  return moment.duration(value, unit).locale("pl").humanize(false, opts);
};
</script>

<style></style>
