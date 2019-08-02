<template>
  <div class="container">
      {{this.$vnode.key}} : 
      <input placeholder="FIRST_NAME" v-model="firstName">
      <input placeholder="LAST_NAME" v-model="lastName">
  </div>
</template>

<script>
export default {
  name: 'ChildDetails',
  props:{
      childId:{
          type:Number,
          default:0
      }
  },
  data:() => {
      return {
          firstName:"",
          lastName:""
      }
  },
  computed:{
      //could put more validation here, I chose to just have atleast a single character
      firstNameValid(){
          return this.firstName.length > 0
      },
      lastNameValid(){
          return this.lastName.length > 0
      },
      // bit of a hacky way to watch 2 things at once.
      fullName(){
          return `${this.firstName} ${this.lastName}`
      }
  },

  watch:{
      // when either of the 2 boxes change, emit an event, as to whether the form is valid or not.
      fullName(){
          if(this.firstNameValid && this.lastNameValid){
              this.$emit("validity",true,this.$vnode.key)
          }
          else{
              this.$emit("validity",false,this.$vnode.key)
          }
      }
  }
}
</script>
