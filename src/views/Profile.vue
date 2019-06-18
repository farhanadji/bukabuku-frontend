<template>
    <div>
    <v-container>
        <!-- <ul v-for="(value, key) in user" :key="key">
            <li>{{ key }}: {{ value }}</li>
        </ul> -->
    <v-layout align-center justify-center column fill-height>
        <v-avatar size="100px">
            <img
                v-if="user.avatar"
                :src="getImage('/'+user.avatar)"
                alt="Avatar"
            >
        </v-avatar>
        <br/>
        <p class="font-weight-medium title">{{user.name}}</p>
        <p class="caption">Username : {{user.username}}</p>
        <p class="caption">Address : {{user.address}}</p>
        <p class="caption">Phone : {{user.phone}}</p>
    </v-layout>

    </v-container>
    </div>
</template>
<script>
import { mapGetters } from 'vuex'
export default {
    computed: {
      ...mapGetters({
        'user':'auth/user'
      }),
    }
}
</script>