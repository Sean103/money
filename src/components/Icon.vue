import Icon from '@/components/Icon.vue';
<template>
    
    <svg class="icon" @click="$emit('click', $event)">
        <use :xlink:href="'#' + name"></use>
    </svg>
    
</template>

<script lang="ts">
   const importAll = (requireContext: __WebpackModuleApi.RequireContext) => requireContext.keys().forEach(requireContext);
   try {
       importAll(require.context('../assets/icons', true, /\.svg$/))
   } catch (error) {
       console.log(error);
       
   }
   // 将一个目录里的任意后缀文件同一全部引入到当前文件
    
    export default {
        name: 'Icon',
        props: ['name']
    }
</script>

<style lang="scss" scoped>
   .icon {
       width: 1em;height: 1em;
       vertical-align: -0.15em;
       fill: currentColor;
       overflow: hidden;
   }

</style>