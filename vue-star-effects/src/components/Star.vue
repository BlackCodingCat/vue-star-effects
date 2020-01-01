<template>
    <div class="stars">
        <div class="star" ref="star" v-for="(item,index) in star_counts" :key="index">
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                star_counts: 800,
                star_distance: 800
            }
        },

        mounted() {
            let _this = this;
            let starsArr = this.$refs.star;
            starsArr.forEach(item => {
                var s = 0.2 + (Math.random() * 1);
                var thisDistance = _this.star_distance + (Math.random() * 300);
                item.style.transformOrigin = `0 0 ${thisDistance}px`
                item.style.transform = `translate3d(0,0,-${thisDistance}px) rotateY(${(Math.random() * 360)}deg) rotateX(${(Math.random() * -50)}deg) scale(${s},${s})`
            });
        },
    }
</script>

<style scoped>

.stars{
    transform: perspective(500);
    transform-style: preserve-3d;
    perspective-origin: 50% 100%;
    position: absolute;
    bottom: 0;
    left: 50%;
    animation: rotate 90s infinite linear;
}


.star{
    width: 2px; height: 2px;
    background: #F7F7B6;
    position: absolute;
    top: 0; left: 0;
    backface-visibility: hidden;
}

@keyframes rotate {
    0% {
        transform: perspective(400px) rotateZ(20deg) rotateX(-40deg) rotateY(0);
    }
    100% {
        transform: perspective(400px) rotateZ(20deg) rotateX(-40deg) rotateY(-360deg);
    }
}
</style>