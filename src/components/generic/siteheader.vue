<template>
  <header>
    <span :class="{'':lSwitchmenu}" class="fixed w-100 cf">
        <nav class="top-0 w-100 cf tc near-white bg-light-pink f7">
            <span class="dn dib-ns fl w-100 pl2 pv2 tl tc-l tracked">
                <small>SIGN UP FOR OUR NEWSLETTER TO GET DISCOUNTS</small>
            </span>

            <span class="dib illusion fade-in absolute-ns right-0 pv2 pr2">
                <i class="fa fa-search mh2"></i>
                <span class="fr">
                    <i class="fa fa-shopping-cart mh2"></i>
                    <span>0</span>
                    <span>0.00 NGN</span>
                </span>
            </span>
        </nav>
        <nav :class="{'bg-white illusion fade-in':lSwitchmenu, 'bg-pink near-white':!lSwitchmenu}" class="tc-l tl w-100 center pa2">
            <img class="h3-l h2" src="@/assets/img/abyalogo.svg" />
            <span class="dn-l"><i class="fa fa-bars f3 fr"/></span>
            <div class="cf w-100 dn db-l">
                <router-link to="/" class="pointer f6 f5-l tracked link mh3 dib pa3 fw3 ttu ph4-l" :class="{'near-black fade-in':lSwitchmenu, 'near-white':!lSwitchmenu}">Home</router-link>
                <router-link to="/shop" class="pointer f6 f5-l tracked link mh3 dib pa3 fw3 ttu ph4-l" :class="{'near-black fade-in':lSwitchmenu, 'near-white':!lSwitchmenu}">
                    <i class="fa fa-shop" /> Shop
                </router-link>
                <router-link to="/brand" class="pointer f6 f5-l tracked link mh3 dib pa3 fw3 ttu ph4-l" :class="{'near-black fade-in':lSwitchmenu, 'near-white':!lSwitchmenu}">Blog</router-link>
                <router-link to="/guide" class="pointer f6 f5-l tracked link mh3 dib pa3 fw3 ttu ph4-l" :class="{'near-black fade-in':lSwitchmenu, 'near-white':!lSwitchmenu}">Cart</router-link>
                <router-link to="/contact" class="pointer f6 f5-l tracked link mh3 dib pa3 fw3 ttu ph4-l" :class="{'near-black fade-in':lSwitchmenu, 'near-white':!lSwitchmenu}">Contact</router-link>
            </div>
        </nav>

    </span>
    <div class="w-100 fl bg-black-50" style="height:76px">&nbsp;</div>
    <div class="w-100 fl bg-black-50 dn db-l" style="height:80px">&nbsp;</div>
  </header>
</template>
<script type="text/javascript">
import menulistitem from "@/components/generic/menulistitem";
import menulistgroup from "@/components/generic/menulistgroup";
const submenu = [
  { to: "/", icon: "", title: "Home" },
  { to: "/story", icon: "", title: "Our Story" },
  { to: "/product", icon: "", title: "Products" },
  { to: "/faq", icon: "", title: "FAQs" },
  { to: "/blog", icon: "", title: "Blog" },
];

export default {
  data() {
    return {
      submenu,
      lShow: false,
      lSwitchmenu: false,
    };
  },
  methods: {
    toggleMenu() {
      this.lShow = !this.lShow;
      //document.getElementsByTagName("html")[0].classList.toggle('overflow-hidden');
    },
    hideMenuOnScroll() {
      var shrinkOn = 50;
      var distanceY = window.pageYOffset || document.documentElement.scrollTop;
      this.lSwitchmenu = (distanceY < shrinkOn) ? false : true;
    },
  },
  components: {
    menulistgroup,
    menulistitem,
  },
  beforeMount() {
      document.documentElement.scrollTop = 0;
      window.addEventListener("scroll", this.hideMenuOnScroll, false);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.hideMenuOnScroll, false);
  },
};
</script>
