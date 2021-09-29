<template>
  <p>
    {{ diff.day }} dagen, {{ diff.hour }} uur, {{ diff.minute }} minuten, {{ diff.second }} seconden
  </p>
</template>

<script>
/*
 * Get the difference between two dates.
 */
const getDateDiff = (date1, date2) => {
  const diff = new Date(date2.getTime() - date1.getTime());
  return {
    year: diff.getUTCFullYear() - 1970,
    month: diff.getUTCMonth(),
    day: diff.getUTCDate() - 1,
    hour: diff.getUTCHours(),
    minute: diff.getUTCMinutes(),
    second: diff.getUTCSeconds(),
  };
};

// App
export default {
  name: "Countdown",
  data() {
    return {
      diff: {},
      timer: undefined,
    };
  },
  props: {
      targetDate: Date
  },
  methods: {
    getDiff() {
      this.diff = getDateDiff(new Date(), this.targetDate);
    },
    formatDate(date) {
      let d = new Date(date),
        month = (d.getMonth() + 1).toString(),
        day = d.getDate().toString(),
        year = d.getFullYear().toString();
      if (month.length < 2) month = "0" + month;
      if (day.length < 2) day = "0" + day;
      return [year, month, day].join("-");
    },
  },
  beforeMount() {
    this.timer = setInterval(this.getDiff, 1000);
  },
  beforeUnmount() {
    clearInterval(this.timer);
  },
};
</script>