<template>
    <article class="flex items-start space-x-6 p-6">
      <img :src="item.image" alt="" class=" object-cover h-48 w-28 flex-none rounded-md bg-slate-100" />
      <div class="min-w-0 relative flex-auto">
        <h2 class="font-semibold text-slate-900 truncate pr-20">{{ item.name }}</h2>
        <dl class="mt-2 flex flex-wrap text-sm leading-6 font-medium">
          <div class="absolute top-0 right-0 flex items-center space-x-1">
            <dt class="flex flex-row text-sky-500">
              <span class="sr-only relative w-5 h-5"></span>
              <svg width="16" height="20" fill="currentColor">
                <path d="M7.05 3.691c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.372 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.539 1.118l-2.8-2.034a1 1 0 00-1.176 0l-2.8 2.034c-.783.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.363-1.118L.98 9.483c-.784-.57-.381-1.81.587-1.81H5.03a1 1 0 00.95-.69L7.05 3.69z" />
              </svg>
            </dt>
            <dd class="text-slate-500" ></dd>
          </div>
        </dl>
        <DescriptionItem :item="item"></DescriptionItem>
        <FeatureItem :item="item"></FeatureItem>
      </div>
    </article>  
</template>
<script> 
  import FeatureItem from '@/components/FeatureItem.vue'
  import DescriptionItem from '@/components/DescriptionItem.vue'

  export default {
    components: {
      FeatureItem,
      DescriptionItem
    },
    props : ['item'],
    methods: {
    goToDetail() {
      this.$router.push('/TourDetail')
    }
  }
}   
</script>     