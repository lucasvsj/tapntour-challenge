<template>

    <div class="bg-black top-10 text-lg pt-10 w-full h-full">
        <div class="flex mb-2" >
         <button @click="$router.go(-1)"  type="submit" class="ml-2">
            <span class="text-white">
             <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18" />
             </svg>
            </span>
        </button>
        <span class="text-xl font-semibold ml-2 " >Cambridge</span>
        </div>
        
        <div class="text-sm text-gray-400 font-light p-5">What action would you like to perform? </div>

        <!-- Payment  -->
        <div class="flex justify-center">
        <button type="button" class="mt-5 border border-gray-200 text-white bg-[#050708] hover:bg-[#050708]/80 focus:ring-4 focus:ring-[#050708]/50 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center dark:hover:bg-[#050708]/40 dark:focus:ring-gray-600 mr-2 mb-2">
            CheckOut with Apple Pay
            <svg class="ml-2 -mr-1 w-5 h-5" aria-hidden="true" focusable="false" data-prefix="fab" data-icon="apple" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512"><path fill="currentColor" d="M318.7 268.7c-.2-36.7 16.4-64.4 50-84.8-18.8-26.9-47.2-41.7-84.7-44.6-35.5-2.8-74.3 20.7-88.5 20.7-15 0-49.4-19.7-76.4-19.7C63.3 141.2 4 184.8 4 273.5q0 39.3 14.4 81.2c12.8 36.7 59 126.7 107.2 125.2 25.2-.6 43-17.9 75.8-17.9 31.8 0 48.3 17.9 76.4 17.9 48.6-.7 90.4-82.5 102.6-119.3-65.2-30.7-61.7-90-61.7-91.9zm-56.6-164.2c27.3-32.4 24.8-61.9 24-72.5-24.1 1.4-52 16.4-67.9 34.9-17.5 19.8-27.8 44.3-25.6 71.9 26.1 2 49.9-11.4 69.5-34.3z"></path></svg>
        </button>
        </div>
        
        <div class="h-20" ></div>
        
    </div>
    <div class="divide-y divide-slate-100 pt-5 cursor-pointer">
      <ListView>
          <p v-if="loading" >Loading details...</p>
          <p v-if="error">{{ error.message }}</p>
          <TourDetailsItem  v-if="details" v-for="(item, index) in details" :key="index" :item="item" />
        </ListView>
    </div>
</template>
<script>
  import { defineComponent, defineProps ,computed } from "vue";
  import { useRoute } from 'vue-router'
  import { storeToRefs } from 'pinia'
  import { useTourStore } from '@/stores/tour'

  import ListView from '@/components/ListView.vue'
  import TourDetailsItem from '@/menu/tour/TourDetailsItem.vue'

  
  export default defineComponent({
    components: {
      ListView,
      TourDetailsItem
    },
    updated() {
      const route = useRoute()
      const { details, loading, error }  = storeToRefs(useTourStore())
      const { fetchTourDetails }       = useTourStore()
      
      console.log(route.params.id)
      fetchTourDetails(route.params.id)
      
      return { details , loading , error }
    },
    setup() {
      const route = useRoute()
      const { details, loading, error }  = storeToRefs(useTourStore())
      const { fetchTourDetails }       = useTourStore()
      
      fetchTourDetails(route.params.id)
      
      return { details , loading , error }
    },
    props : ['item'],
    methods: {
  }
});   
</script>