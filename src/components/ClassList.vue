<template>
  <div class="">
      <!-- create the forms for each child --> 
      <ChildDetails v-for="child in children" :key="child.id"  v-on:validity="updateValidity"/>

      {{(allValid ? "ALL CHILDREN ARE VALID" : "NOT ALL CHILDREN ARE VALID")}}
  </div>
</template>

<script>

import ChildDetails from "./ChildDetails"
export default {
  name: 'ClassList',
  data:() => {
      return {
          //perhaps label them here or something, can be strings
          children:[{
              id:0,
              valid:false
          },
          {
              id:1,
              valid:false
          },
          {
              id:2,
              valid:false
          }]
      }
  },
  computed:{
      // all this does is tell us whether all of the children above, have `valid:true`
      allValid(){
          const validity = this.children.map(child => {
              return child.valid
          });

          return validity.indexOf(false) === -1
      }
  },
  methods:{
      updateValidity(isValid,key){
        // all this does is look for the child with key, and change it to the result of 
        // isValid
        for(let i = 0; i < this.children.length;i++){
            const child = this.children[i];
            if(child.id === key){
                this.children[i]['valid'] = isValid;
            }
        }
      }
  },
  components:{
      ChildDetails
  },
}
</script>
