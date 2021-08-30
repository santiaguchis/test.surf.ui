<template>
    <div class="container">
        <swiper
            :slides-per-view="1"
            :space-between="40"
            :breakpoints="breakpoints"
            @swiper="onSwiper"
            @touchMove="onTouchMove"
            @touchEnd="onTouchEnd"
            @slideChange="onSlideChange">
            <swiper-slide class="item animate"
                v-for="( item , index ) in rows"
                :key="index">
                <SurfCard :data="item" />
            </swiper-slide>
        </swiper >
    </div>
</template>
<script>
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/swiper.min.css';
import Data from '@/data.json';
import SurfCard from './Card.vue';
export default {
    name : 'SurfBox',
    components : {
        Swiper,
        SwiperSlide,
        SurfCard
    },
    setup() {
        const onSwiper = (swiper) => {
            console.log(swiper);
        };
        const onTouchEnd = ( swiper , event ) => {
            console.log( 'Touch End' )
            document.body.classList.remove('drag-move')
        };
        const onTouchMove = ( swiper , event ) => {
            console.log( 'init' )
            document.body.classList.add('drag-move')
        };
        const onSlideChange = () => {
            console.log('slide change');
        };
        const breakpoints = {
            "320": {
                "slidesPerView": 2,
                "spaceBetween": 20
            },
            "991": {
                "slidesPerView": 3,
                "spaceBetween": 40
            },
            "1280": {
                "slidesPerView": 4,
                "spaceBetween": 50
            }
        };
        const rows = Data.surf
        return {
            onSwiper,
            onSlideChange,
            onTouchMove,
            onTouchEnd,
            breakpoints,
            rows
        };

    },
}
</script>
<style lang="scss" scoped>
.container {
    padding: 30px;
    .swiper-slide {
        transform: translateY( 35vh );
    }
    .swiper-slide + .swiper-slide {
        transform: translateY( 35vh );
    }
    .swiper-slide-active {
        transform: translateY( 10vh ) !important;
    }
    .swiper-slide-next  {
        transform: translateY( 0 ) !important;
    }
    .swiper-slide-next + .swiper-slide {
        transform: translateY( 20vh ) !important;
    }
    .swiper-container {
        overflow: visible !important;
    }
}
</style>