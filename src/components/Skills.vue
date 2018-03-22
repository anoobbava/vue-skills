<template>
  <div class="hello">
    <div class="holder">
     <ul>
      <form @submit.prevent="addSkill">

        <input type="text" placeholder="Enter the skill you have.." v-model="dataInput" v-validate="'min: 5'" name="skill">

        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class= "animated flipOutX">

          <p class="alert" v-if="errors.has('skill')">{{errors.first('skill')}}</p>

        </transition>
      </form>

      <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
        <li v-for="(data, index) in skills" :key='index'>
          {{data.skill}}
          <i class="fa fa-minus-circle" v-on:click="removeData(index)"></i>
        </li>
      </transition-group>
       <p>These are the Skills you posses</p>
     </ul>
    </div>


  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      dataInput: '',
      skills: [
                {'skill': 'Ruby'},
                { 'skill': 'Rails'}
              ]
    }
  },
  methods: {
    addSkill(){
      this.$validator.validateAll().then((result) => {
        if(result){
          this.skills.push({skill: this.dataInput});
          this.dataInput = '';
        }
        else{
          alert('Not authorised');
        }
      })
    },
    removeData(id){
      this.skills.splice(id, 1);
    }
  }

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
  @import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";
    input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687F7F;
  }

  .holder {
    background: #fff;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }

  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    /*border-right:5px solid #675667;*/
    margin-bottom: 4px;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }

  .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }

  .alert-in-enter-active{
    animation: bounce-in .5s;
  }

  .alert-in-leave-active{
    animation: bounce-in .5s reverse;
  }

  @keyframes bounce-in {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1.2);
    }
    100% {
      transform: scale(1);
    }
  }

  i {
    float: right;
    cursor:pointer;
  }

</style>

<!-- https://coursetro.com/posts/code/138/vue -->
<!-- https://coursetro.com/courses/23/Vue-Tutorial-in-2018---Learn-Vue.js-by-Example/lessons/6 -->
