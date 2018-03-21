<template>
  <div class="hello">
    <div class="holder">
     <ul>
       <li v-for="(data, index) in skills" :key='index'>{{data.skill}}</li>
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
      skills: [
                {'skill': 'Ruby'},
                { 'skill': 'Rails'},
                { 'skill': 'vue'},
                {'skill': 'html'},
                {'skill': 'CSS'}
              ]
  } }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

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

</style>
