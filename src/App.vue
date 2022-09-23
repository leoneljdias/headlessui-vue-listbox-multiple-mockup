<template>
  <div id="app">
    <div className="flex items-center justify-center p-12">
      <div className="w-full max-w-xs mx-auto">
        <MultiSelect :options="list" v-model="selected" />
        <pre class="mt-8 text-sm text-left">{{ selected }}</pre>
      </div>
    </div>
  </div>
</template>

<script>
import MultiSelect from "@/components/MultiSelect";

export default {
  name: "App",
  data() {
    return {
      selected: [],
      list: [
        {
          name: "Alberta",
          code: "AB",
        },
        {
          name: "British Columbia",
          code: "BC",
        },
        {
          name: "Manitoba",
          code: "MB",
        },
        {
          name: "New Brunswick",
          code: "NB",
        },
        {
          name: "Newfoundland and Labrador",
          code: "NL",
        },
        {
          name: "Nova Scotia",
          code: "NS",
        },
        {
          name: "Northwest Territories",
          code: "NT",
        },
        {
          name: "Nunavut",
          code: "NU",
        },
        {
          name: "Ontario",
          code: "ON",
        },
        {
          name: "Prince Edward Island",
          code: "PE",
        },
        {
          name: "Quebec",
          code: "QC",
        },
        {
          name: "Saskatchewan",
          code: "SK",
        },
        {
          name: "Yukon",
          code: "YT",
        },
      ],
    };
  },
  components: {
    MultiSelect,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
