<template>
  <div style="background: #f5ece3">
    <mobile-nav v-if="mobileView" class="m_nav"></mobile-nav>
    <div class="main" :class="{ open: ShawNav }">
      <navbar-vue
        :title="title"
        style="border-bottom: 1px solid #55555555"
        v-if="!mobileView"
      ></navbar-vue>
      
      <mobileNavBarVue
        :title="title"
        :ShawNav="ShawNav"
        v-if="mobileView"
        @makeShow="makeShow"
      ></mobileNavBarVue>
      <h1 class="intro">Our contacts</h1>
    </div>
    <contact-vue></contact-vue>
    <div class="wrapper">
      <img class="map" src="@/images/map.png" alt="" />
    </div>
    <my-footer></my-footer>
  </div>
</template>

<script>
import NavbarVue from "@/components/UI/Navbar.vue";
import contactVue from "@/components/UI/contact.vue";
import MyFooter from "@/components/MyFooter.vue";
import MobileNav from "@/components/UI/MobileNav.vue";
import mobileNavBarVue from "@/components/UI/mobileNavBar.vue";
export default {
  components: {
    mobileNavBarVue,
    MobileNav,
    NavbarVue,
    contactVue,
    MyFooter,
  },
  data() {
    return {
      mobileView: false,
      ShawNav: false,
      title: [
        { color: "color: #555555", img: require("@/images/profile_black.png") },
        { color: "color: #555555", img: require("@/images/shop_black.png") },
        { color: "color: #555555", img: require("@/images/search_black.png") },
        { color: "color: #555555", img: require("@/images/menu_black.png") },
      ],
    };
  },
  methods: {
    handleView() {
      this.mobileView = window.innerWidth <= 900;
    },
    makeShow() {
      this.ShawNav = !this.ShawNav;
    },
  },
  created() {
    this.handleView();
    window.addEventListener("resize", this.handleView);
  },
};
</script>

<style scoped>
.m_nav {
  position: absolute;
  top: 3rem;
}
.wrapper {
  display: flex;
  width: 100%;
  height: fit-content;
  justify-content: center;
  padding: 50px 0 50px 0;
  align-content: center;
}
.main {
  width: 100%;
  border-radius: 10px;
  overflow: hidden;
  position: relative;
  background-image: url(@/images/image1.png);
  background-size: cover;
  transition: 1s transform cubic-bezier(0, 0.12, 0.14, 1);
  background: #f5ece3;
}
.intro {
  color: #555555;
  text-align: center;
  font-size: 40px;
  margin-top: 100px;
  letter-spacing: 2px;
}
.map {
  max-width: 1000px;
  max-height: 550px;
}

.open {
  transform: translateX(160px);
}

@media (min-width: 901px) {
  .open {
    transform: translateX(0);
  }
}
</style>