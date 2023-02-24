

<template>
        
        <div class="">
          <div class="text-left">
            
            <button
              @click="isOpen = true"
              class="font-medium text-indigo-900"
              type="button"
            >
             see example
            </button>
      
            <div
              v-show="isOpen"
              class="
                absolute
                inset-0
                flex
                items-center
                justify-center
                bg-gray-700 bg-opacity-50
                overflow-hidden
              "
            >
              <div class="max-w-xl object-cover p-6 bg-white rounded-md ">
                <div class="flex items-center justify-between">
                  <h3 class="text-xl">Student Verification Example</h3>
                  <svg
                    @click="isOpen = false"
                    xmlns="http://www.w3.org/2000/svg"
                    class="w-8 h-8 text-black cursor-pointer"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z"
                    />
                  </svg>
                </div>
                <div class="mt-4 border">
                  <img src="../assets/images/example.png" alt="" class="object-fit">
                 
                  
                </div>
                <button
                @click="isOpen = false"
                class="px-6 py-2 bg-indigo-900 text-white border rounded mt-5 rounded-full align-center"
              >
                Close
              </button>
              </div>
            </div>
          </div>
        </div>
</template>
<style scoped>
    
</style>
<script>
  export default {
    data() {
    return {
      isOpen: false,
    };
  },
}
</script>