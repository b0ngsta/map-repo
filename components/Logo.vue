<template>
  <div class="VueToNuxtLogo">
    <v-container>
      <v-row>
    <v-col cols="12" sm="6" md="3">
      <v-text-field
              label="First Name"   
      ></v-text-field>
    </v-col>
    <v-col cols="12" sm="6" md="3">
      <v-text-field
              label="Last Name"
      ></v-text-field>
    </v-col>
    <v-col cols="12" sm="6" md="3">
      <v-text-field
              label="City"
              v-model="searchKey"
      ></v-text-field>
    </v-col>
    <v-btn rounded style="margin-left: 10px; padding: 20px; margin-top: 10px;"  @click="addNew">search</v-btn>
    </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
    data: function(){
        return{
            searchKey: '',
            
        }
    },
  
  methods: {
    addNew(){
            this.$emit('addEd',this.searchKey);
            
    }
  }
}
</script>


<style>
</style>
