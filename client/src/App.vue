<template>
  <v-app style="background: #E3E3EE">
    <v-navigation-drawer app temporary fixed v-model="sideNav"> 
      <v-toolbar color="accent" dark flat>
        <v-toolbar-side-icon @click="toggleSideNav"></v-toolbar-side-icon>
        <router-link to="/" tag="span" style="cursor: pointer">
          <h1 class="title" pl-3>PhotoHost</h1>
        </router-link>
      </v-toolbar>
        
        <v-divider></v-divider>

        <v-list>
          <v-list-tile ripple v-for="item in sideNavItems" :key="item.title" :to="item.link">
            <v-list-tile-action>
              <v-icon>{{item.icon}}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              {{item.title}}
            </v-list-tile-content>
          </v-list-tile>
        </v-list>

    </v-navigation-drawer>
    <v-toolbar fixed color="primary" dark>
      <v-toolbar-side-icon @click="toggleSideNav"></v-toolbar-side-icon>
      <v-toolbar-title class="hidden-xs-only">
        <router-link to="/" tag="span" style="cursor: pointer">
        PhotoHost
        </router-link>
      </v-toolbar-title>
      
      <v-spacer></v-spacer>

      <v-text-field flex prepend-icon="search" placeholder="Search Posts Or Images" color="grey" single-linehide-details>   
      </v-text-field>

      <v-spacer></v-spacer>

      <v-toolbar-items class="hidden-xs-only">
        <v-btn flat v-for="item in horisontalNavItems" :key="item.title" :to="item.link">
          <v-icon class="hidden-sm-only" left>{{item.icon}}</v-icon>
          {{item.title}}
          
        </v-btn>
      </v-toolbar-items>
      </v-toolbar>

          <main>
           <v-container class="mt-4">
            <transition name="fade">
              <router-view/>
            </transition>
           </v-container>
          </main>
  </v-app>
</template>


<script>
export default {
  name: "App",
  data() {
    return {
      sideNav: false
    };
  },
  computed: {
    horisontalNavItems() {
      return [
        { icon: "chat", title: "Posts", link: "/posts" },
        { icon: "camera_alt", title: "Images", link: "/images" },
        { icon: "lock", title: "Log In", link: "/login" },
        { icon: "create", title: "Register", link: "/register" }
      ];
    },

    sideNavItems() {
      return [
        { icon: "chat", title: "Posts", link: "/posts" },
        { icon: "camera_alt", title: "Images", link: "/images" },
        { icon: "lock", title: "Log In", link: "/login" },
        { icon: "create", title: "Register", link: "/register" }
      ];
    }
  },
  methods: {
    toggleSideNav() {
      this.sideNav = !this.sideNav;
    }
  }
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition-property: all;
  transition-duration: 0.25s;
}

.fade-enter-active {
  transition-delay: 0.25s;
}

.fade-enter,
.fade-leave-active {
  opacity: 0;
  transform: translateY(-25px);
}
</style>