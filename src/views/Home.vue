<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2> {{ message2 }} </h2>
    <body>
      <button v:on-click>Click away</button>
    </body>
  </div>
</template>
<style></style>
<script>
export default {
  data: function() {
    return {
      message: "HEY",
      message2: "WELCOME"
    };
  },
  created: function() {},
  methods: {

  }
};
</script>