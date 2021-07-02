<template>
    <div class="wrapper-dices">
        <div id="dice-1" class="dice">
                <div class="spinner " v-bind:class="'dice-' + dices[0]">
                    <div class="face1">1</div>
                    <div class="face2">2</div>
                    <div class="face3">3</div>
                    <div class="face4">4</div>
                    <div class="face5">5</div>
                    <div class="face6">6</div>
                </div>
            </div>
            <div id="dice-2" class="dice">
                <div class="spinner" v-bind:class="'dice-' + dices[1]">
                    <div class="face1">1</div>
                    <div class="face2">2</div>
                    <div class="face3">3</div>
                    <div class="face4">4</div>
                    <div class="face5">5</div>
                    <div class="face6">6</div>
                </div>
            </div>
    </div>
</template>
<script>
export default {
    name: 'dices',
    data() {
        
    },
    props:{
        dices:  { type: Array, default: (2, 2) }
        // dices:Array
    }
}
</script>
<style>
.spinner {
    -webkit-transform-style: preserve-3d;
    -ms-transform-style: preserve-3d;
    transform-style: preserve-3d;
    -webkit-transform-origin: 60px 60px 0;
    -ms-transform-origin: 60px 60px 0;
    transform-origin: 60px 60px 0;
    -webkit-transition: all .9s ease;
    -o-transition: all .9s ease;
    transition: all .9s ease;
    -webkit-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    -ms-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    -o-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
	transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
}
.spinner.dice-1 {
	-webkit-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    -ms-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    -o-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
}
.spinner.dice-2 {
	-webkit-transform: rotateX(0deg) rotateY(-90deg) rotateZ(0deg);
    -ms-transform: rotateX(0deg) rotateY(-90deg) rotateZ(0deg);
    -o-transform: rotateX(0deg) rotateY(-90deg) rotateZ(0deg);
    transform: rotateX(0deg) rotateY(-90deg) rotateZ(0deg); 
}
.spinner.dice-3 {
    -webkit-transform: rotateX(0deg) rotateY(-90deg) rotateZ(90deg);
    -ms-transform: rotateX(0deg) rotateY(-90deg) rotateZ(90deg);
    -o-transform: rotateX(0deg) rotateY(-90deg) rotateZ(90deg);
    transform: rotateX(0deg) rotateY(-90deg) rotateZ(90deg); 
}
.spinner.dice-4 {
    -webkit-transform: rotateX(0deg) rotateY(180deg) rotateZ(90deg);
    -ms-transform: rotateX(0deg) rotateY(180deg) rotateZ(90deg);
    -o-transform: rotateX(0deg) rotateY(180deg) rotateZ(90deg);
    transform: rotateX(0deg) rotateY(180deg) rotateZ(90deg); 
}
.spinner.dice-5 {
    -webkit-transform: rotateX(0deg) rotateY(90deg) rotateZ(0deg);
    -ms-transform: rotateX(0deg) rotateY(90deg) rotateZ(0deg);
    -o-transform: rotateX(0deg) rotateY(90deg) rotateZ(0deg);
    transform: rotateX(0deg) rotateY(90deg) rotateZ(0deg); 
}
.spinner.dice-6 {
    -webkit-transform: rotateX(90deg) rotateY(90deg) rotateZ(0deg);
    -ms-transform: rotateX(90deg) rotateY(90deg) rotateZ(0deg);
    -o-transform: rotateX(90deg) rotateY(90deg) rotateZ(0deg);
    transform: rotateX(90deg) rotateY(90deg) rotateZ(0deg); 
}
</style>