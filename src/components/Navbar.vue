<template>
    <div>
        <v-app-bar flat app>
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-app-bar-title class="text-uppercase blue--text">
                <span class="font-weight-light">Todo</span>
                <span>Ninja</span>
            </v-app-bar-title>
            <v-spacer></v-spacer>
            <v-btn text color="red lighten-2">
                <span>Sign Out</span>
                <v-icon>exit_to_app</v-icon>
            </v-btn>

            <v-navigation-drawer v-model="drawer" temporary app class="indigo">
                <p>test</p>
            </v-navigation-drawer>
        </v-app-bar>
    </div>
</template>

<script>
export default {
    data() {
        return {
            drawer: false
        }
    },
}
</script>

<style scoped>

</style>