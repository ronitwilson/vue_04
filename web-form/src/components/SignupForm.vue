<template>
  <form>
      <label> Email :</label>
      <input type="email" required v-model="email">
      <label> Password :</label>
      <input type="password" required v-model="password">

      <label>Role:</label>
      <select v-model="role">
        <option value="Developer">Developer</option>
        <option value="Senior Developer">Senior developer</option>
      </select>

      <div class="terms">
        <input type="checkbox" required v-model="terms" >
        <label> Accept terms and conditions </label>
      </div>

      <p > Please choose the tech where you have experiences</p>
      <div>
        <input type="checkbox" value="REACT" v-model="teck_exp">
        <label> REACT  </label>
      </div>
        <div>
        <input type="checkbox" value="Vue" v-model="teck_exp">
        <label> Vue </label>
      </div>
        <div>
        <input type="checkbox" value="JAVA" v-model="teck_exp">
        <label> JAVA </label>
      </div>
      <div>
        <label>Other skills</label>
        <input input="text" v-model="temp_skill" @keyup.alt="addSkill">
      </div>

      <div v-for="skill in skills" :key="skill" class="pill">
      <p @click="deleteSkill(skill)">{{skill}}</p>
      </div>

  </form>
  <p> Email is {{ email }}</p>
  <p> Password is {{ password }}</p>
  <p> Role is {{ role }}</p>
  <p> Terms accepted is {{ terms }}</p>
  <p> Tech exp is {{ teck_exp }}</p>
  <p> skill set is {{ skills }}</p>
  
  </template>
  
  <script>
  export default {
    name: 'SignupForm',
    data() {
      return {
        email: '',
        password: '',
        role: 'Developer',
        terms: true,
        teck_exp: [],
        temp_skill: '',
        skills: []
      }
    },
    methods: {
      addSkill($event) {
        console.log($event)
        if($event.key === ',' && this.temp_skill) {
          if (! this.skills.includes(this.temp_skill)) {
            this.skills.push(this.temp_skill)
          }
          this.temp_skill = ''
        }
      },
      deleteSkill(skill) {
        this.skills = this.skills.filter(item => {
          return item !== skill
        })
      }
    }
  }
  
  </script>
  
  <style>
    form {
      max-width: 420px;
      margin: 30px auto;
      background: white;
      text-align: left;
      padding: 40px;
      border-radius: 10px;
    }
    label {
      color: #aaa;
      display: inline-block;
      margin: 25px 0 15px;
      font-size: 0.6em;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: bold;
    }
    input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }
  input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
  }
  my_paragraph {
      display: inline-block;
      margin: 25px 0 15px;
      font-size: 0.6em;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: bold;
    }
    .pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
  </style>
