<template>
  <div class="profile-card">
    <p class="text-center">
      <img
        :src="activeUser.avatar"
        alt=""
        class="avatar-xlarge img-update"
      >
    </p>

    <div class="form-group">
      <input
        v-model="activeUser.username"
        type="text"
        placeholder="Username"
        class="form-input text-lead text-bold"
      >
    </div>

    <div class="form-group">
      <input
        v-model="activeUser.name"
        type="text"
        placeholder="Full Name"
        class="form-input text-lead"
      >
    </div>

    <div class="form-group">
      <label for="user_bio">Bio</label>
      <textarea
        id="user_bio"
        v-model="activeUser.bio"
        class="form-input"
        placeholder="Write a few words about yourself."
      />
    </div>

    <div class="stats">
      <span>{{ activeUser.postsCount }} post{{ activeUser.postsCount !== 1 ? 's' : '' }}</span>
      <span>{{ activeUser.threadsCount }} thread{{ activeUser.threadsCount !== 1 ? 's' : '' }}</span>
    </div>

    <hr>

    <div class="form-group">
      <label
        class="form-label"
        for="user_website"
      >Website</label>
      <input
        id="user_website"
        v-model="activeUser.website"
        autocomplete="off"
        class="form-input"
      >
    </div>

    <div class="form-group">
      <label
        class="form-label"
        for="user_email"
      >Email</label>
      <input
        id="user_email"
        v-model="activeUser.email"
        autocomplete="off"
        class="form-input"
      >
    </div>

    <div class="form-group">
      <label
        class="form-label"
        for="user_location"
      >Location</label>
      <input
        id="user_location"
        v-model="activeUser.location"
        autocomplete="off"
        class="form-input"
      >
    </div>

    <div class="btn-group space-between">
      <button
        class="btn-ghost"
        @click.prevent="cancel"
      >
        Cancel
      </button>
      <button
        type="submit"
        class="btn-blue"
        @click.prevent="save"
      >
        Save
      </button>
    </div>
  </div>
</template>

<script>
import { mapStores } from 'pinia'
import { useUsersStore } from '../stores/users'

export default {
  props: {
    user: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      activeUser: {...this.user}
    }
  },
  computed: {
    ...mapStores(useUsersStore)
  },
  methods: { 
    save() {
      this.usersStore.updateUser({...this.activeUser})
      // this.usersStore.updateUser({...this.activeUser}, userId) ? Maybe
      this.$router.push({ name: 'Profile' })
    },
    cancel() {
      this.$router.push({ name: 'Profile' })
    }
  }
}
</script>

<style scoped>
  
</style>