<template>
    <div class="card" :class="( item.active ) ? 'active' : ''">
        <button class="btn-close animate" @click="closeOverImages()">
            <span>Close</span> <i class="mdi mdi-close"></i>
        </button>
        <div class="picture animate">
            <div class="list-images animate">
                <div class="item-img">
                    <img src="../assets/surf/modelo-2021-soft-01.png" :alt="item.alt" class="">
                </div>
            </div>
            <div class="paginate animate">
                <buton class="btn-page animate active">
                    01
                </buton>
                <buton class="btn-page animate">
                    02
                </buton>
                <buton class="btn-page animate">
                    03
                </buton>
                <buton class="btn-page animate">
                    04
                </buton>
            </div>
        </div>
        <div class="circle-mask animate "  @click="activeItem()">
        </div>
        <div class="caption animate">
            <div class="info">
                <h3 class="title" v-text="item.title"></h3>
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
    position: relative;
    width: 320px;
    overflow: hidden;
    height: 320px;
    box-shadow: 0px 0px 2px 0px rgba($color: #000000, $alpha: 0.9);
    .brand {
        position: absolute;
        left: 15px;
        top: 15px;
        font-size: 13px;
        font-weight: 400;
        visibility: visible;
        opacity: 1;
    }
    .circle-mask {
        // transform: scale( 1.5 , 1.5 ) translate(35% , -35% );
        border: 250px solid rgba($color: white, $alpha: 1.0);
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
            border: 4px solid rgba($color: #000000, $alpha: 1.0);
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
            transform: translate(60px , 30px) scale(1.3);
            
            .item-img {
                width: 100%;
                text-align: center;
                img {
                    display: inline-block;
                    margin: 30px auto 0;
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
        padding: 10px 15px;
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
            line-height: 28px;
            height: 28px;
            width: 28px;
            font-size: 14px;
        }
    }
    .paginate {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        padding: 0 10px 10px;
        visibility: hidden;
        opacity: 0;
        z-index: 1;
        .btn-page {
            background: transparent;
            border: 0 none transparent;
            color: white;
            display: inline-block;
            position: relative;
            font-size: 20px;
            text-align: center;
            vertical-align: bottom;
            font-weight: 400;
            margin: 0 10px;
            transform-origin: 0 100%;
            font-weight: 200;
            font-family: Arial;
            transition-delay: 0s;
            opacity: 0;
            visibility: hidden;
            transform: scale(1,1) translateY(20px);
            top: 20px;
            &:nth-child(1) {
                transition-delay: .5s;
            }
            &:nth-child(2) {
                transition-delay: .75s;
            }
            &:nth-child(3) {
                transition-delay: 1s;
            }
            &:nth-child(4) {
                transition-delay: 1.25s;
            }
            &:before {
                content: " ";
                display: block;
                background: transparent;
                border: 1px solid rgba($color: #FFFFFF, $alpha: 0.75);
                width: 100%;
                height: 8px;
                position: absolute;
                bottom: -1px;
                left: 0;
                right: 0;
                border-radius: 50%;
                opacity: 0;
                visibility: hidden;
            }
            &.active {
                font-size: 32px;
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
        width: calc( 100% - 30px );
        height: auto;
        position: absolute;
        bottom: 0;
        left: 0;
        align-self: center;
        padding: 15px;
        right: 0;
        visibility: visible;
        opacity: 1;
        z-index: 3;
        .title {
            font-family: 'Alegreya', serif;
            font-size: 24px;
            font-weight: 400;
        }
        .price {
            font-size: 14px;
            display: inline-block;
            vertical-align: middle;
            font-weight: 500;
            &:before {
                content: "$";
                font-family: 'Alegreya', serif;
                font-weight: 400;
                font-size: 20px;
            }
        }
        .btn-cart {
            width: 32px;
            height: 32px;
            margin-left: 8px;
            border: 1px solid rgba($color: #000000, $alpha: 0.8);
            border-radius: 50%;
            display: inline-block;
            cursor: pointer;
            vertical-align: middle;
            background: transparent;
        }
    }
}
</style>