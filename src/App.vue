<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer"
    app>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h3">
            Contacts
          </v-list-item-title>
          <v-list-item-subtitle>
            Your contacts
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
       
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Stay Connected</v-toolbar-title>
    </v-app-bar>
    
    <!-- App bar -->
    <v-app-bar
      
      color="primary"
      dark
      src="https://picsum.photos/1920/1080?random"
      app
      prominent

    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>App</v-app-bar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-phone</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-account-reactivate</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main >

      <!-- If using vue-router -->
      <router-view></router-view>
  
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({ drawer: null,
      items: [
          { title: 'Contact list', icon: 'mdi-account-box', to: '/' },
          { title: 'About App', icon: 'mdi-help-box', to: '/about' },]
    
    }),
    
    
  }
</script>