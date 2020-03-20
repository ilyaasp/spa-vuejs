<template>
    <div class="container">
        <div class="user">
            <h2> Data user dengan nama : {{ user.name }} </h2>
            <ul>
                <li> Username : {{ user.username }} </li>
                <li> Email : {{ user.email }} </li>
                <li> Address : {{ user.address.street }}, {{user.address.city}} </li>
                <li> Phone : {{ user.phone }} </li>
                <li> Website : {{ user.website }} </li>
                <li> Company : {{ user.company.name }} </li>
            </ul>
            <router-link to="/"> Back </router-link>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
      return {
          user: []
      }
  },
  created() {
      this.getUser()
  },
  methods: {
      getUser() {
          axios.get(`https://jsonplaceholder.typicode.com/users/${this.$route.params.id}`)
          .then((response) => {
            this.user = response.data
          })
          .catch((err) => {
            console.log(err)     
          })
      }
  }
}
</script>

<style scoped>
ul li {
    list-style: none;
}
.container{
    background: blueviolet;
}

router-link{
    opacity: 1;
    visibility: visible;
    border-left-color: #4DB6AC;
    margin: 10px;
    transition: all 0.25s;
}
</style>