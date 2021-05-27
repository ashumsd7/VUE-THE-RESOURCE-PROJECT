<template>
    <the-header :title="headerTitle"></the-header>
  
   <TheResource/>
</template>

<script>

import TheHeader from   './components/layouts/TheHeader'
import TheResource from   './components/learning-resources/TheResources'
export default {
  components: {
    // LearningResource,
    // StoredResource,
    TheHeader,
    TheResource
  },
  data() {
    return {
      headerTitle:"The Learning App",
     
    };
  }
};
</script>


<style >
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>