<template>
  <section>
    <siteheader/>
    <shopbanner />
    <div class="fl w-100 pa3">
        <div class="cf mw9 center w-100 pa3">
            <div class="f7 ttu w-100 fl">
                HOME <i class="mh1 fa fa-chevron-right"/> BRAND
            </div>
                
            <div class="tc w-100 mv4">
                <span class="cf f3 center bb b--near-black tracked">BRAND</span>
            </div>
        </div>
    </div> 
    <div class="w-100 mw9 center cf"> 
        <div class="fl w-100 pv4">
            <article class="fl w-30-ns w-100 bg-white br3 pa3 pa1-ns mv3 b--black-10">
                <div class="tc">
                    <img src="https://static.wixstatic.com/media/e79a11_208c9230c87e447681577eace3adac31~mv2.jpeg/v1/crop/x_0,y_9,w_545,h_594/fill/w_276,h_302,al_c,q_80,usm_0.66_1.00_0.01/Efaghene.webp" class=" br1 dib ba b--black-05 pa2" title="">
                    <h1 class="f3 mb2">Ese Efagene</h1>
                    <h2 class="f5 fw4 mt0">MD/CEO</h2>
                </div>
            </article>

            <article class="fl w-60-ns w-100 bg-white br3 pa3 pa1-ns mv3 b--black-10">
                <div class="">
                    <h2 class="f5 fw4 lh-copy mt0">
                        My vision for Xclassy Lingerie & Apparels was borne out of the simple need of providing women of all sizes with a place where they can shop for their intimate apparel without facing the lack of privacy associated with purchasing intimate apparel from open markets.<br><br> 
                        At Xclassy Lingerie & Apparels, we understand that due to the lack of privacy in the open markets, women are forced to buy their intimate apparel in sizes that do not accentuate or look good on their particular body type. We aim to change this narrative.<br>
                        Xclassy Lingerie & Apparels seek to provide women with a place where women can safely, privately and comfortably shop for their intimate apparel without the hassle associated with purchasing such garments in open markets. We cater to the needs of every woman regardless of age, weight or sense of style. At Xclassy Lingerie & Apparels, we specialize in undergarments that bring out the sexy goddess in every woman.<br> 
                        When it comes to quality and unique designs, think Xclassy. We have something for everyone!<br>
                        We stock the finest lingerie, brassier, pants, sleepwear, and shape-wears that will tingle your senses and appeal to your aesthetics. If you're looking for something naughty and sassy, we've got you covered.<br>
                        The best part is that our goods are quite affordable! whether you are a working-class lady, a housewife or a student, you can always find something classy yet sexy that fits your budget and sense of style perfectly.<br><br> 
                        Welcome to our world of affordable luxury where you can freely explore and have it all... literally.<br>
                        At Xclassy Lingerie & Apparel, we simply believe lingerie is your intimate poetry made manifest...
                    </h2>
                </div>
            </article> 
        </div>
        
        <div class="fl w-100 pv4">
     
            <div class="w-third-ns w-100 fl pa1"> 
                <div class="w-100 pa3 vh-50" style="width:100%;background:#fbcbc9">
                    <article class="mw5 center br3 pa3 pa4-ns mv3">
                        <div class="tc">
                            <img src="@/assets/img/testimonial.jpg" class="br-100 h3 w3 dib" title="">
                            <h1 class="f4">Alice Temperley</h1>
                            <hr class="mw3 bb bw1 b--black-10">
                        </div>
                        <p class="lh-copy measure center f6 black-70">
                            "I think it's what is worn underneath that really inspires a woman to feel beautiful in her clothes".
                        </p>
                    </article>
                </div>
            </div>           
            
            <div class="w-third-ns w-100 fl pa1"> 
                <div class="w-100 pa3 vh-50 bg-near-white" >
                   <article class="mw5 center br3 pa3 pa4-ns mv3">
                        <div class="tc">
                            <img src="@/assets/img/testimonial.jpg" class="br-100 h3 w3 dib" title="">
                            <h1 class="f4">Dolce & Gabbana</h1>
                            <hr class="mw3 bb bw1 b--black-10">
                        </div>
                        <p class="lh-copy measure center f6 black-70">
                            “Lingerie is the maximum expression of a woman's femininity.”
                        </p>
                    </article>
                </div>
            </div>

             <div class="w-third-ns w-100 fl pa1"> 
                <div class="w-100 pa3 vh-50" style="width:100%;background:#fbcbc9">
                    <article class="mw5 center br3 pa3 pa4-ns mv3">
                        <div class="tc">
                            <img src="@/assets/img/testimonial.jpg" class="br-100 h3 w3 dib" title="">
                            <h1 class="f4">Nicole Richie</h1>
                            <hr class="mw3 bb bw1 b--black-10">
                        </div>
                        <p class="lh-copy measure center f6 black-70">
                            “I think lingerie plays a big part in how you carry yourself.”
                        </p>
                    </article>
                </div>
            </div>

           
            
        </div>

        <featureditems title="NEW ARRIVALS"/>

    </div>

    <sitefooter/>
  </section>
</template>

<script type="text/javascript">
import { HTTP } from "@/common";
import { checkRedirect } from "@/common";
import siteheader from "@/components/generic/siteheader";
import shopbanner from "@/components/generic/shopbanner";
import featureditems from "@/components/generic/featureditems";
import newsletter from "@/components/generic/newsletter";
import sitefooter from "@/components/generic/sitefooter";

export default {
  components: {
    siteheader, featureditems, newsletter, sitefooter, shopbanner
  },
  data() {
    return {
      lLoading: true,
      notifications: [],
      username: "",
      password: "",
      IsCompany: true,
      hoverMember:false,
      slides: [
      'https://lorempixel.com/800/400/food/1',
      'https://lorempixel.com/800/400/food/2',
      'https://lorempixel.com/800/400/food/3',
      'https://lorempixel.com/800/400/food/4',
      'https://lorempixel.com/800/400/food/5',      
    ],
    current: 0,
    width: 800,
    timer: 0,
    };
  },
  methods: {
    nextSlide: function() {
      this.current++;
      if (this.current >= this.slides.length)
        this.current = 0;
      this.resetPlay();
    },

    prevSlide: function() {
      this.current--;
      if (this.current < 0)
        this.current = this.slides.length - 1;
      this.resetPlay();
    },

    selectSlide: function(i) {
      this.current = i;
      this.resetPlay();
    },

    resetPlay: function() {
      clearInterval(this.timer);
      this.play();
    },

    play: function() {
      let app = this;
      this.timer = setInterval(function() {
        app.nextSlide();
      }, 2000);
    },
    created: function() {
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
          password: this.password
        },
        {
          withCredentials: true
        }
      )
        .then(response => {
          this.notifications.push(response.data);
          setTimeout(checkRedirect(response.data), 2000);
        })
        .catch(e => {
          console.log(e);
          this.error = e;
          // this.errors.push(e)
        });
    }
  }
};
</script>


<style>
  * {box-sizing: border-box;}
  .mySlides {display: none;}
  img {vertical-align: middle;}

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
    from {opacity: .4} 
    to {opacity: 1}
  }

  @keyframes fade {
    from {opacity: .4} 
    to {opacity: 1}
  }

  /* On smaller screens, decrease text size */
  @media only screen and (max-width: 300px) {
    .text {font-size: 11px}
  }
</style>
