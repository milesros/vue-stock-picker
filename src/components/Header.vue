<template>
<nav class="navbar navbar-default">
  <div class="container-fluid">
    <div class="navbar-header">
       <router-link class="navbar-brand" to="/">Stock Trader</router-link>
    </div>
    <div class="collapse navbar-collapse">
      <ul class="nav navbar-nav">
        <router-link to="/portfolio" activeClass="active"  tag="li"><a>Portfolio</a></router-link>
        <router-link to="/stocks"  activeClass="active" tag="li"><a>Stocks</a></router-link>
      </ul>
      <strong class='navbar-text navbar-right'>Funds: {{funds | currency}}</strong>
      <ul class="nav navbar-nav navbar-right">
        <li><a href="#" @click='endDay'>End Day</a></li>
        <li class='dropdown' @click="isDropdownOpen = !isDropdownOpen" :class="{open: isDropdownOpen}">
          <a href="#" class='dropdown-toggle' 
            data-toggle='dropdown' role='button' 
            aria-haspopup="true" 
            aria-expanded="false"> Save & load <span class="caret"></span></a>
          <ul class="dropdown-menu">
            <li><a href="#">Save</a></li>
            <li><a href="#">Load</a></li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</nav>
</template>

<script>
import {mapActions} from 'vuex';
export default {
  data(){
    return{
      isDropdownOpen: false
    }
  },
  methods:{
    ...mapActions([
      'randomizeStocks'
    ]),
    endDay(){
      this.randomizeStocks();
    } 
  },
  computed: {
    funds() {
      return this.$store.getters.funds;
    }
  }
};
</script>

