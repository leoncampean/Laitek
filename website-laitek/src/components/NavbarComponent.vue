<template>
  <ul>
    <router-link to="/Home">
      <li>
        <a
          v-on:click="isActive = !isActive"
          v-bind:class="{ active: isActive }"
          class="submenu homeMenu"
          >Home
        </a>
      </li>
    </router-link>
    <router-link to="/Patiens">
      <li><a v-show="isAdmin" class="submenu patiensMenu">Patients</a></li>
    </router-link>
    <router-link to="/Users">
      <li><a class="submenu cusersMenu">Users</a></li>
    </router-link>
    <router-link v-show="isAdmin" to="/Admins">
      <li><a class="submenu adminMenu">Admin</a></li>
    </router-link>
    <router-link to="/profile">
      <li><a class="submenu logout" >Pofile</a></li>
    </router-link>
    <router-link to="/">
      <li style="float: right"><a class="submenu logout" @click="logoutClick()" >Logout {{user.username}}</a></li>
    </router-link>
    
  </ul>
</template>

<script>


let loggedUser= JSON.parse(localStorage.getItem('logedUser'));

export default {
  data() {
    return {
      user: loggedUser,
      isAdmin: loggedUser.role == 'admin'
    }
  
  },
  methods: {
    logoutClick() {
      localStorage.removeItem("loggedUser");
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  margin: auto;
  padding: 0;
  overflow: hidden;
  background-color: #333;
  margin-bottom: 20px;
  width: 90%;
}

li {
  float: left;
}

li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li a:hover:not(.active) {
  background-color: #111;
}

.active {
  background-color: #04aa6d;
}
</style>