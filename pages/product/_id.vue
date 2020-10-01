<template>
  <div>
    Picture :{{ this.$route.params.id.links[0].href }} <br><br>
    Title : {{ this.$route.params.id.data[0].title }} <br><br>
    Description : {{ this.$route.params.id.data[0].description }} <br><br>
    Keywords : {{ this.$route.params.id.data[0].keywords }} <br><br>
  </div>
</template>
