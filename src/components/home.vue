<template>
  <section>
    <siteheader />
    <div
      class="fl vh-100 dt w-100 bg-dark-gray white cover"
      style="background:url(https://cdn.shopify.com/s/files/1/1463/5092/files/Ofuure_Swimsuit_Website_Banner_1_847b9e21-48c4-41ec-a04f-a62581ef9030_1296x.jpg?v=1596202446) no-repeat center;"
    >
      <div class="dtc v-mid pl3">
        <div class="w5 pa3 bg-white-80 br2 tl near-black">
          <div class="f3 fw6 ttu tracked mb2 lh-title">#NEW ARRIVALS</div>
          <div class="f6 ttu tracked mb2 lh-title">Shop our new arrivals</div>
          <button class="bg-black br1 pa3 bn near-white f5">SHOP NOW</button>
        </div>
      </div>
    </div>
    <div class="w-100 mw9 center cf">
      <featureditems title="NEW ARRIVALS" />

      <div class="fl w-100 pv4">
        <div class="w-50 fl pa1">
          <div class="w-100 pa3 vh-50" style="width:100%;background:#e75874">
            <div class="dt w-100 h-100 bg-black-20">
              <div class="dtc v-mid tc pointer">
                <button
                  class="center pointer hover-black br1 pv2 ph3 bn near-white f5"
                  style="background:#322514"
                >SHOP NOW</button>
              </div>
            </div>
          </div>
        </div>

        <div class="w-50 fl pa1">
          <div class="w-100 pa3 vh-50" style="width:100%;background:#fbcbc9">
            <div class="dt w-100 h-100 bg-black-20">
              <div class="dtc v-mid tc pointer">
                <button
                  class="center pointer hover-black br1 pv2 ph3 bn near-white f5"
                  style="background:#e75874"
                >SHOP NOW</button>
              </div>
            </div>
          </div>
        </div>

        <div class="w-50 fl pa1">
          <div class="w-100 pa3 vh-50" style="width:100%;background:#be1558">
            <div class="dt w-100 h-100 bg-black-20">
              <div class="dtc v-mid tc pointer">
                <button
                  class="center pointer hover-black br1 pv2 ph3 bn near-black f5"
                  style="background:#fbcbc9"
                >SHOP NOW</button>
              </div>
            </div>
          </div>
        </div>

        <div class="w-50 fl pa1">
          <div class="w-100 pa3 vh-50" style="width:100%;background:#322514">
            <div class="dt w-100 h-100 bg-black-20">
              <div class="dtc v-mid tc pointer">
                <button
                  class="center pointer hover-black br1 pv2 ph3 bn near-black f5"
                  style="background:#fbcbc9"
                >SHOP NOW</button>
              </div>
            </div>
          </div>
        </div>
      </div>

      <featureditems title="Featured collection" />
    </div>
    <sitefooter />
  </section>
</template>

<script type="text/javascript">
import { HTTP } from "@/common";
import { checkRedirect } from "@/common";
import siteheader from "@/components/generic/siteheader";
import featureditems from "@/components/generic/featureditems";
import sitefooter from "@/components/generic/sitefooter";

export default {
  components: {
    siteheader,
    featureditems,
    sitefooter,
  },
  data() {
    return {
      lLoading: true,
      notifications: [],
      username: "",
      password: "",
      IsCompany: true,
      hoverMember: false,
      slides: [
        "https://lorempixel.com/800/400/food/1",
        "https://lorempixel.com/800/400/food/2",
        "https://lorempixel.com/800/400/food/3",
        "https://lorempixel.com/800/400/food/4",
        "https://lorempixel.com/800/400/food/5",
      ],
      current: 0,
      width: 800,
      timer: 0,
    };
  },
  methods: {
    nextSlide: function () {
      this.current++;
      if (this.current >= this.slides.length) this.current = 0;
      this.resetPlay();
    },

    prevSlide: function () {
      this.current--;
      if (this.current < 0) this.current = this.slides.length - 1;
      this.resetPlay();
    },

    selectSlide: function (i) {
      this.current = i;
      this.resetPlay();
    },

    resetPlay: function () {
      clearInterval(this.timer);
      this.play();
    },

    play: function () {
      let app = this;
      this.timer = setInterval(function () {
        app.nextSlide();
      }, 2000);
    },
    created: function () {
      this.play();
    },
    goToPage() {
      if (this.IsCompany) {
        this.$router.push({ name: "companies" });
      } else {
        this.$router.push({ name: "vendors" });
      }
    },
    keyUp(event) {
      if (event.code == "Enter") {
        this.login();
      }
    },
    login() {
      HTTP.post(
        "/api/login",
        {
          username: this.username,
          password: this.password,
        },
        {
          withCredentials: true,
        }
      )
        .then((response) => {
          this.notifications.push(response.data);
          setTimeout(checkRedirect(response.data), 2000);
        })
        .catch((e) => {
          console.log(e);
          this.error = e;
          // this.errors.push(e)
        });
    },
  },
};
</script>


<style>
* {
  box-sizing: border-box;
}
.mySlides {
  display: none;
}
img {
  vertical-align: middle;
}

/* Slideshow container */
.slideshow-container {
  max-width: 1000px;
  position: relative;
  margin: auto;
}

/* Caption text */
.text {
  color: #f2f2f2;
  font-size: 15px;
  padding: 8px 12px;
  position: absolute;
  bottom: 8px;
  width: 100%;
  text-align: center;
}

/* Number text (1/3 etc) */
.numbertext {
  color: #f2f2f2;
  font-size: 12px;
  padding: 8px 12px;
  position: absolute;
  top: 0;
}

/* The dots/bullets/indicators */
.dot {
  height: 15px;
  width: 15px;
  margin: 0 2px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}

.active {
  background-color: #717171;
}

/* Fading animation */
.fade {
  -webkit-animation-name: fade;
  -webkit-animation-duration: 1.5s;
  animation-name: fade;
  animation-duration: 1.5s;
}

@-webkit-keyframes fade {
  from {
    opacity: 0.4;
  }
  to {
    opacity: 1;
  }
}

@keyframes fade {
  from {
    opacity: 0.4;
  }
  to {
    opacity: 1;
  }
}

/* On smaller screens, decrease text size */
@media only screen and (max-width: 300px) {
  .text {
    font-size: 11px;
  }
}
</style>
