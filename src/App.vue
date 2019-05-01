<template>
  <div id="app">
    <link
      rel="stylesheet"
      href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700,400italic|Material+Icons"
    />
    <md-button class="md-raised md-primary" @click="dialogToggle"
      >dialog</md-button
    >
    <transition>
      <div class="dialog" v-drag v-if="isShow" :style="dialogStyle">
        <div class="dialog__header">
          <span>User</span
          ><i class="material-icons dialog__close" @click="dialogToggle">
            clear
          </i>
        </div>
        <md-table v-model="users" md-card>
          <md-table-row slot="md-table-row" slot-scope="{ item }">
            <md-table-cell md-label="ID" md-sort-by="id" md-numeric>{{
              item.id
            }}</md-table-cell>
            <md-table-cell md-label="Name" md-sort-by="name">{{
              item.name
            }}</md-table-cell>
            <md-table-cell md-label="Email" md-sort-by="email">{{
              item.email
            }}</md-table-cell>
          </md-table-row>
        </md-table>
      </div>
    </transition>
  </div>
</template>

<script>
import drag from "@branu-jp/v-drag";

export default {
  name: "App",
  data() {
    return {
      isShow: false,
      dialogStyle: {
        top: 16 + "px",
        right: 16 + "px"
      },
      users: [
        {
          id: 1,
          name: "Shawna Dubbin",
          email: "sdubbin0@geocities.com"
        },
        {
          id: 2,
          name: "Odette Demageard",
          email: "odemageard1@spotify.com"
        },
        {
          id: 3,
          name: "Lonnie Izkovitz",
          email: "lizkovitz3@youtu.be"
        },
        {
          id: 4,
          name: "Thatcher Stave",
          email: "tstave4@reference.com"
        },
        {
          id: 5,
          name: "Clarinda Marieton",
          email: "cmarietonh@theatlantic.com"
        }
      ]
    };
  },
  methods: {
    dialogToggle: function() {
      this.isShow = !this.isShow;
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 16px;
}
.dialog {
  position: absolute;
  width: 420px;
  box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.2);
  background-color: #fff;
  z-index: 99999;
  border-radius: 2px;
  border: 1px solid #f0f0f0;
  cursor: move;
  &__header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #f0f0f0;
    padding: 8px 16px;
  }
  &__close {
    cursor: pointer;
  }
}
</style>
