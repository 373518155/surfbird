<template>
    <modal name="profile-modal" @before-open="beforeOpen">
        <h1>{{ $t('modal.profile.title') }}</h1>

        <p>
            <label for="profile-name">{{ $t('modal.profile.name') }}</label>
            <input type="text" for="profile-name" v-model="profileName"/>
        </p>

        <p>
            <button @click="createProfile">{{ $t('modal.profile.create') }}</button>
        </p>
    </modal>
</template>

<script>
    export default {
      name: 'profile-modal',
      data: function () {
        return {
          profileName: ''
        }
      },
      methods: {
        beforeOpen () {
          this.profileName = ''
        },
        createProfile () {
          this.$store.dispatch('addProfile', this.profileName)
          this.$modal.hide('profile-modal')
        }
      }
    }
</script>

<style>

</style>
