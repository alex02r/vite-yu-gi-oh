<script>
export default {
    
}
</script>
<template lang="">
    <div class="loader-container">
        <span class="loader"></span>
    </div>
    
</template>
<style lang="scss" scoped>
    @use '../styles/generals.scss';
    .loader-container{
        height: 80vh;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .loader {
        width: 48px;
        height: 48px;
        border: 5px solid black;
        border-bottom-color: transparent;
        border-radius: 50%;
        display: inline-block;
        box-sizing: border-box;
        animation: rotation 1s linear infinite;
        }
    
        @keyframes rotation {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
        } 
    
</style>