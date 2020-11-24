<template>
    <section>
        <siteheader />
        <shopbanner />
        <div class="fl w-100 pa3">
            <div class="cf mw9 center w-100 pa3">
                <div class="f7 ttu w-100 fl">
                    HOME <i class="mh1 fa fa-chevron-right"/> CATEGORY BEING VIEWED
                </div>
                    
                <div class="tc w-100 mv4">
                    <span class="cf f3 center bb b--near-black tracked">CATEGORY BEING VIEWED</span>
                </div>
                
                <div class="f6 w-100 fl pb4">
                    <div class="fl" style="width:12rem"> 
                        <span class="ph2 pointer fl w-100" @click="lSortby = !lSortby">Sort <i class="fr mr4 fa fa-chevron-down"/> </span>

                        <div class="fl w-100 relative" @click="lSortby = !lSortby">
                            <ul :class="{'slide-bottom':lSortby,'dn':!lSortby}" class="bg-white z-3 absolute w-100 pa0 ma0 list ">
                                <li class="pa2 ph3 bt b--white-10 hover-bg-dark-gray hover-near-white pointer" v-for="(sort, index) in sortList" :key="index">
                                    {{sort.Title}}
                                </li>
                            </ul>

                        </div>
                    </div>
                </div>


                <div class="flex flex-wrap w-100 ">
                    <div class="fl w-25-l w-50-m w-100 h-100" v-for="(product, index) in productList" :key="index">
                        <div class="dt w-100 h-100 ph1" style="height:45vh">
                            <div class="dtc v-mid tc bg-light-gray pointer" @mouseenter="product.Focus=true" @mouseleave="product.Focus=false">
                                <router-link to="/view_product" v-if="product.Focus" class="center bg-black pointer hover-bg-light-pink hover-black br1 pa2 bn near-white f6 no-underline">Quick View</router-link>  
                            </div>
                        </div>
                        <div class="w-100 fl tc bg-white f6 pa2"> 
                            {{product.Title}} <span class="db">{{product.Price}} {{product.Currency}}</span>
                        </div>
                    </div>
                </div>

            </div>
        </div>
        <sitefooter />
    </section>
</template>

<script type="text/javascript">
import { HTTP } from "@/common";
import { checkRedirect } from "@/common";
import siteheader from "@/components/generic/siteheader";
import shopbanner from "@/components/generic/shopbanner";
import featureditems from "@/components/generic/featureditems";
import sitefooter from "@/components/generic/sitefooter";

export default {
    components: {
        siteheader, shopbanner, featureditems, sitefooter,
    },
    data() {return {
        notifications: [], lSortby: false,
        sortList: [
            {Code:"featured", Title:"Featured", Params:{}},
            {Code:"pricelow", Title:"Price, low to high", Params:{}},
            {Code:"pricehigh", Title:"Price, high to low", Params:{}},
            {Code:"alphabeta", Title:"Alphabetically, A-Z", Params:{}},
            {Code:"alphabetz", Title:"Alphabetically, Z-A", Params:{}},
            {Code:"dateold", Title:"Date, old to new", Params:{}},
            {Code:"datenew", Title:"Date, new to old", Params:{}},
            {Code:"bestselling", Title:"Best Selling", Params:{}},
        ],
        productList:[
            {Focus:false, Title:"Sample Product", Price:"1000", Currency:"NGN" },
            {Focus:false, Title:"Sample Product", Price:"1000", Currency:"NGN" },
            {Focus:false, Title:"Sample Product", Price:"1000", Currency:"NGN" },
            {Focus:false, Title:"Sample Product", Price:"1000", Currency:"NGN" },
            {Focus:false, Title:"Sample Product", Price:"1000", Currency:"NGN" },

            
        ],
    }},
    methods: {
        
    },
};
</script>

