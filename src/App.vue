<template>
  <table
    class="table is-bordered is-striped is-narrow is-hoverable is-fullwidth"
  >
    <thead>
      <tr>
        <th @click="sortBystring">رشته ها</th>
        <th @click="sortBynumber">اعداد</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in itmes" :key="item.number">
        <td>{{ item.string }}</td>
        <td>{{ item.number }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      itmes: [
        { string: "Four", number: 4 },
        { string: "One", number: 1 },
        { string: "Two", number: 2 },
        { string: "Five", number: 5 },
        { string: "three", number: 3 },
      ],
      descNumber: false,
      descString: false,
    };
  },
  methods: {
    sortBynumber() {
      if (this.descNumber) {
        this.itmes.sort((a, b) => {
          //نزولی نشان دادن
          return b.number - a.number;
        });
      } else {
        this.descNumber = true;
        this.itmes.sort((a, b) => {
          //صعودی نشان دادن عدد
          return a.number - b.number;
        });
      }
    },
    sortBystring() {
      if (this.descString) {
        this.descString = false;
        this.itmes.sort((a, b) => {
          if (a.string.toLowerCase() < b.string.toLowerCase()) return 1;
          if (a.string.toLowerCase() > b.string.toLowerCase()) return -1;

          return 0;
        });
      } else {
        this.descString = true;
        this.itmes.sort((a, b) => {
          if (a.string.toLowerCase() < b.string.toLowerCase()) return -1;
          if (a.string.toLowerCase() > b.string.toLowerCase()) return 1;

          return 0;
        });
      }
    },
  },
};
</script>
