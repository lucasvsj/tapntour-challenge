<template>
  <div class="w-full mt-2">
    <div class="flex items-top justify-between text-slate-500 text-sm text-justify " >
      {{ item.resume || item.bio }}
    </div>   
  </div>
</template>
<script> 
  export default {
    props : ['item'],
    
    methods: {
      
  }
}   
</script>    