<template>
  <header
    id="header"
    class="header"
  >
    <router-link
      :to="{ name: 'Home' }"
      class="logo"
    >
      <img src="../assets/img/svg/vueschool-logo.svg">
    </router-link>

    <div class="btn-hamburger">
      <!-- use .btn-humburger-active to open the menu -->
      <div class="top bar" />
      <div class="middle bar" />
      <div class="bottom bar" />
    </div>

    <!-- use .navbar-open to open nav -->
    <nav class="navbar">
      <ul>
        <li class="navbar-user">
          <router-link :to="{ name: 'Profile' }">
            <img
              class="avatar-small"
              :src="authUser.avatar"
              alt=""
            >
            <span>
              {{ authUser.name }}
              <img
                class="icon-profile"
                src="../assets/img/svg/arrow-profile.svg"
                alt=""
              >
            </span>
          </router-link>

          <!-- dropdown menu -->
          <!-- add class "active-drop" to show the dropdown -->
          <div id="user-dropdown">
            <div class="triangle-drop" />
            <ul class="dropdown-menu">
              <li class="dropdown-menu-item">
                <a href="profile.html">View profile</a>
              </li>
              <li class="dropdown-menu-item">
                <a href="#">Log out</a>
              </li>
            </ul>
          </div>
        </li>
      </ul>

      <ul>
        <!-- <li class="navbar-item">
          <a href="index.html">Home</a>
        </li>
        <li class="navbar-item">
          <a href="category.html">Category</a>
        </li>
        <li class="navbar-item">
          <a href="forum.html">Forum</a>
        </li>
        <li class="navbar-item">
          <a href="thread.html">Thread</a>
        </li> -->
        <!-- Show these option only on mobile-->
        <!-- <li class="navbar-item mobile-only">
          <a href="profile.html">My Profile</a>
        </li>
        <li class="navbar-item mobile-only">
          <a href="#">Logout</a>
        </li> -->
      </ul>
    </nav>
  </header>
</template>

<script>
import { mapStores } from 'pinia'
import { useAuthUserStore } from '../stores/authUser'

export default {
  computed: {
    authUser() {
      return this.authUserStore.authUser
    },
    ...mapStores(useAuthUserStore)
  }
}
</script>

<style lang="">
  
</style>