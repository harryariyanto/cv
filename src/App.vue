<template>

 <v-app>
   <link href="https://fonts.googleapis.com/css?family=Material+Icons" rel="stylesheet">
  <!-- <v-toolbar app>
    <v-icon medium>
widgets
    </v-icon>
  <div class="display-1 font1">
      Harry's Portfolio 
    </div> 
   
  </v-toolbar> -->
  <v-content>
    <div style="min-width:800px;">
<maincontent >
  </maincontent>
</div>
  </v-content>
  <!-- <v-footer app>
    
  </v-footer> -->
</v-app>
</template>

<script>
import maincontent from './components/maincontent'

     
export default {
  name: 'App',
  components: {
    maincontent
  },
  data () {
    return {
      //
    }
  }
}
</script>
<style>
.font1{
  font-family: 'Righteous', cursive !important;
}


</style>

