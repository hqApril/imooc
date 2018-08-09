<template>
	<div>
		<Nav v-bind:logo-src="logoSrc" />
		<router-view v-on:logoSrc="changeLogoSrc"></router-view>
		<Footer />
	</div>
</template>


<script>
import Nav from '@/components/Nav';
import router from './router';
import Footer from '@/components/Footer';

export default {
  name: 'App',
  data() {
	  return {
		  logoSrc: "../../static/img/logo.png"
	  }
  },
  components: {
	  Nav,
	  Footer
  },
  methods: {
		changeLogoSrc(src) {
			this.logoSrc = src;
		}
  }
}
</script>

<style>
* {
	padding: 0;
	margin: 0;
	box-sizing: border-box;
}

a {
	text-decoration: none;
}

ul {
	list-style: none;
}

@font-face {
	font-family: icomoon;
	src: url('../static/font/icomoon.ttf');
}
</style>
