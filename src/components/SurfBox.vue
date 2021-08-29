<template>
    <div class="container">
        <div class="item"
            v-for="( item , index ) in rows"
            :key="index">
            <SurfCard :data="item" />
        </div>
    </div>
</template>
<script>
import SurfCard from './SurfCard.vue';
export default {
    name : 'SurfBox',
    components : {
        SurfCard
    },
    data() {
        return {
            rows : [
                {
                    title : 'Soft',
                    picture : null,
                    images : [
                        {
                            src : '../assets/surf/modelo-2021-soft-01.png',
                            alt : 'Imagen de tabla de surf, modelo Soft 2021 Foto de arriba',
                            srcset : 'assets/surf/modelo-2021-soft-01.png, assets/surf/modelo-2021-soft-01@2x.png x2'
                        },
                        {
                            src : '../assets/surf/modelo-2021-soft-02.png',
                            alt : 'Imagen de tabla de surf, modelo Soft 2021 Foto de abajo',
                            srcset : 'assets/surf/modelo-2021-soft-02.png, assets/surf/modelo-2021-soft-02@2x.png x2'
                        },
                        {
                            src : '../assets/surf/modelo-2021-soft-03.png',
                            alt : 'Imagen de tabla de surf, modelo Soft 2021 Foto de lado',
                            srcset : 'assets/surf/modelo-2021-soft-03.png, assets/surf/modelo-2021-soft-03@2x.png x2'
                        }
                    ],
                    price : 1.599,
                    brand : 'Brusurf'
                }
            ]
        }
    }
}
</script>
<style lang="scss" scoped>
.container {
    padding: 30px;
}
</style>