<template>
    <div class="card" 
        :class="( item.active ) ? 'active' : ''">
        <div class="inner">

            <button class="btn-close animate" @click="closeOverImages()">
                <span>Close</span> <i class="mdi mdi-close"></i>
            </button>
            <div class="picture animate">
                <div class="list-images animate">
                    <div class="item-img" v-if="item.images && item.images.length">
                        <img :src="item.images[0].src" :alt="item.images[0].alt" class="">
                    </div>
                </div>
                <div class="paginate animate">
                    <button class="btn-page animate active"
                        v-for="( page, index ) in item.images"
                        :key="index">
                        {{ index + 1 }}
                    </button>
                </div>
            </div>
            <div class="circle-mask animate "  @click="activeItem()">
            </div>
            <div class="caption animate">
                <div class="info">
                    <h3 class="title" v-text="item.name"></h3>
                    <div class="recommended"></div>
                </div>
                <div class="cart">
                    <span class="price">{{ toCurrency( item.price ) }}</span>
                    <button class="btn-cart">
                        <i class="mdi mdi-basket-outline"></i>
                    </button>
                </div>
            </div>
            <h4 class="brand animate" v-text="item.brand"></h4>
        </div>
    </div>
</template>
<script>
export default {
    props : [
        'data'
    ],
    data() {
        return {
            item : {}
        }
    },
    methods : {
        toCurrency( val ) {
            return  `${ val }`;
        },
        activeItem() {
            this.item.active = true
        },
        closeOverImages() {
            this.item.active = false
        }
    },
    mounted() {
        this.item = this.data
    }
}
</script>
<style lang="scss" scoped>
.card {
    display: block;
    padding: 1rem;
    .inner {
        position: relative;
        width: 30rem;
        overflow: hidden;
        height: 30rem;
        box-shadow: 0px 0px 0.2rem 0px rgba($color: #000000, $alpha: 0.9);

    }
    .brand {
        position: absolute;
        left: 1.5rem;
        top: 1.5rem;
        font-size: 1.5rem;
        font-weight: 400;
        max-width: 8rem;
        visibility: visible;
        opacity: 1;
    }
    .circle-mask {
        // transform: scale( 1.5 , 1.5 ) translate(35% , -35% );
        border: 25rem solid rgba($color: white, $alpha: 1.0);
        position: absolute;
        left: -52%;
        right: 0;
        border-radius: 50%;
        bottom: 0;
        top: -182%;
        width: 180%;
        height: 180%;
        &:before {
            content: " ";
            border: .2rem solid rgba($color: #000000, $alpha: 0.5);
            position: absolute;
            left: 0;
            right: 0;
            border-radius: 50%;
            bottom: 0;
            top: 0;
        }
    }
    .picture {
        display: block;
        background: moccasin;
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        top: 0;
        &:hover {
            border-bottom-left-radius: 0%;
        }
        .list-images {
            width: 100%;
            transform: translate(6rem , 3rem) scale(1.3);
            
            .item-img {
                width: 100%;
                text-align: center;
                img {
                    display: inline-block;
                    margin: 3rem auto 0;
                    width: 70%;
                    height: auto;
                }
            }
        }
    }
    &.active {
        .picture {
            background: rgba($color: #333333, $alpha: 1);
        }
        .circle-mask {
            transform: scale(2);
        }
        .brand ,
        .caption {
            visibility: hidden;
            opacity: 0;
        }
        .list-images {
            transform: translate(0 , 0) scale(1);
        }
        .paginate,
        .btn-close {
            visibility: visible;
            opacity: 1;
        }
        .paginate {
            .btn-page {
                transform: translateY(0);
                opacity: 1;
                visibility: visible;
                top: 0;
            }
        }
    }
    .btn-close {
        background: transparent;
        top: 0;
        right: 0;
        position: absolute;
        padding: 1rem 1.5rem;
        color: white;
        border: 0 none transparent;
        visibility: hidden;
        opacity: 0;
        z-index: 1;
        span {
            display: inline-block;
            vertical-align: middle;
        }
        .mdi {
            display: inline-block;
            vertical-align: middle;
            border: 1px solid white;
            color: white;
            border-radius: 50%;
            line-height: 2.8rem;
            height: 2.8rem;
            width: 2.8rem;
            font-size: 14px;
        }
    }
    .paginate {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        padding: 0 1rem 1rem;
        visibility: hidden;
        opacity: 0;
        z-index: 1;
        .btn-page {
            background: transparent;
            border: 0 none transparent;
            color: white;
            display: inline-block;
            position: relative;
            font-size: 2rem;
            text-align: center;
            vertical-align: bottom;
            font-weight: 400;
            margin: 0 1rem;
            transform-origin: 0 100%;
            font-weight: 200;
            font-family: Arial;
            transition-delay: 0s;
            opacity: 0;
            visibility: hidden;
            transform: scale(1,1) translateY(20px);
            top: 20px;
            &:nth-child(1) {
                transition-delay: .4s;
            }
            &:nth-child(2) {
                transition-delay: .5s;
            }
            &:nth-child(3) {
                transition-delay: .6s;
            }
            &:nth-child(4) {
                transition-delay: .7s;
            }
            &:before {
                content: " ";
                display: block;
                background: transparent;
                border: 1px solid rgba($color: #FFFFFF, $alpha: 0.75);
                width: 100%;
                height: .8rem;
                position: absolute;
                bottom: -1px;
                left: 0;
                right: 0;
                border-radius: 50%;
                opacity: 0;
                visibility: hidden;
            }
            &.active {
                font-size: 3.2rem;
                &:before {
                    opacity: 1;
                    visibility: visible;
                }
            }
        }
    }
    .caption {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: calc( 100% - 3rem );
        height: auto;
        position: absolute;
        bottom: 0;
        left: 0;
        align-self: center;
        padding: 1.5rem;
        right: 0;
        visibility: visible;
        opacity: 1;
        z-index: 3;
        .title {
            font-family: 'Alegreya', serif;
            font-size: 2.4rem;
            font-weight: 400;
        }
        .price {
            font-size: 1.4rem;
            display: inline-block;
            vertical-align: middle;
            font-weight: 500;
            &:before {
                content: "$";
                font-family: 'Alegreya', serif;
                font-weight: 400;
                font-size: 2rem;
            }
        }
        .btn-cart {
            width: 3.2rem;
            height: 3.2rem;
            margin-left: .8rem;
            border: .1rem solid rgba($color: #000000, $alpha: 0.8);
            border-radius: 50%;
            display: inline-block;
            cursor: pointer;
            vertical-align: middle;
            background: transparent;
        }
    }
}
</style>