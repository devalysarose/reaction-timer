<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        <p>Click Me</p>
    </div>
</template>

<script>
export default {
    props:['delay'] ,
    data(){
        return{
            showBlock:false,
            reactionTime:0           
        }
    },
    mounted(){  
        console.log(this.delay)  
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer()
        }, this.delay);
        
       
    },
    methods:{  
        startTimer(){
            setInterval(() => {
                this.reactionTime += 10
            }, 10)
        } ,   
        stopTimer(){            
            this.showBlock = false;
            clearInterval(this.reactionTime);
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
.block{
    width: 400px;
    height: 200px;
    background-color: rgb(65, 165, 65);
    border-radius: 10px;
    border: 1px solid green;
    margin-top: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
}
</style>