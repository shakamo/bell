<template>
  <nb-container>
    <nb-header>
      <nb-left>
        <nb-button transparent>
          <nb-icon :name="'menu'" />
        </nb-button>
      </nb-left>
      <nb-body>
        <nb-title>Headeraa</nb-title>
      </nb-body>
      <nb-right />
    </nb-header>

    <nb-content>
      <nb-icon name='home' />
      <nb-icon ios="ios-menu" android="md-menu" :style="{ fontSize: 20, color: 'red' }" />
      <nb-icon type="FontAwesome" name="home" />
      <nb-list>
        <nb-list-item v-for="item in items" :key="item">
          <nb-text>{{item}}</nb-text>
        </nb-list-item>
      </nb-list>
    </nb-content>

  </nb-container>
</template>
 
<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
</style>

<script>
import Vue from "vue-native-core";
import { StackNavigator } from "vue-native-router";
import { VueNativeBase } from "native-base";
import { AppLoading } from "expo";
// registering all native-base components to the global scope of the Vue
Vue.use(VueNativeBase);
export default {
  components: { AppLoading },
  data: function() {
    return {
      isAppReady: false,
      items: [
        "Simon Mignolet",
        "Nathaniel Clyne",
        "Dejan Lovren",
        "Mama Sakho",
        "Emre Can"
      ]
    };
  },
  created: function() {
    this.loadFonts();
  },
  methods: {
    loadFonts: async function() {
      try {
        this.isAppReady = false;
        await Expo.Font.loadAsync({
          Roboto: require("native-base/Fonts/Roboto.ttf"),
          Roboto_medium: require("native-base/Fonts/Roboto_medium.ttf"),
          Ionicons: require("@expo/vector-icons/fonts/Ionicons.ttf")
        });
        this.isAppReady = true;
      } catch (error) {
        console.log("some error occured", error);
        this.isAppReady = true;
      }
    }
  }
};
</script>
