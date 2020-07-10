<template>
  <div class="container">
    <div class="holder">
      
      <form @submit.prevent='addSkill'>
        <input type="text" placeholder="Enter a skill you have.." v-model="skill">
        {{ skill }}
        <transition enter-active-class='animate__flipInX' leave-active-class='animate__flipOutX'>
          <p class="alert" v-if="skill.length<3&&skill.length>0"> Skill must be greater than 3 characters</p>
        </transition>
      </form>

      <ul>
          <li v-for="(data, index) in skills" v-bind:key='index'>{{data.skill}}</li>
      </ul>
      
      <p>These are the skills that you possess.</p>
    
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skill: '',
      skills: [
        {"skill" : 'Programming Languages - HTML5, CSS3, JavaScript(ES6), C++(STLs), Node Js, Java, MongoDB'},
        {"skill" : 'Programming Frameworks - Vue.js, Express.js, Bootstrap 4'},
        {"skill" : 'Tools - Github'},
        {"skill" : 'Frontend Development'},
        {"skill" : 'Backend Development'},
      ]
    }
  },
  methods: {
    addSkill() {
      if(this.skill.length >= 3) {
        this.skills.push({skill: this.skill})
        this.skill = ''
      }
    }
  }
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
    margin-bottom: 2px;
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

  input {
    width: calc(100%  - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687f7f;
  }
  .alert {
    background: #ff2b00;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
    color: white;
  }
</style>
