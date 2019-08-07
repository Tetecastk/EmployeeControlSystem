<template>
  <div id="app">
    <h1>{{ title }}</h1>
    <div class="container">
      <div class="row">
        <div class="mb-4">
           <font-awesome-icon icon="user" />
           <font-awesome-icon icon="search"></font-awesome-icon>
           <font-awesome-icon icon="edit"></font-awesome-icon>
           <font-awesome-icon icon="trash-alt"></font-awesome-icon>
        </div>
        <div class="mb" v-for="employee of employees">
          <ul>
            <li>{{ employee.id }} - 
                {{ employee.employee_name }} - 
                {{ employee.employee_salary }} - 
                {{ employee.employee_age }} - 
                {{ employee.profile_image }}
            </li>
          </ul>
        </div>
      </div>
      <div class="row">
        <div class="mb">
          One of three columns
        </div>
        <div class="mb">
          One of three columns
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      title: 'Employee Control System',
      employees: []
    }
  },

  created () {
     this.axios
      .get('http://dummy.restapiexample.com/api/v1/employees')
      .then(response => response.data)
      .then(employees => this.employees = employees)
      .catch(error => console.log(error));
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css?family=Blinker:400,600&display=swap');

#app {
  /*font-family: 'Avenir', Helvetica, Arial, sans-serif;*/
  font-family: 'Blinker', sans-serif;
  font-weight: 400;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  width: 100%;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
