<script setup>

</script>

<template>
  <div class="relative h-screen	">
			<div class="bg-white pt-10 pb-14 sm:pt-16 lg:pt-24 lg:pb-24">
			  <div class="mx-auto max-w-5xl lg:px-8">
				<div class="lg:flex">
					<div class="hidden lg:block">
						<img class="w-[100%]" src="./assets/images/te.png" alt="" /></div>
				  		<div class="mx-auto max-w-md px-4 text-center sm:max-w-2xl sm:px-6 lg:flex lg:px-0 lg:text-left">
						<div class="lg:py-24">

					
					  <h1 class="text-2xl text-left font-bold tracking-tight sm:mt-5 sm:text-3xl ">
						Statement Of Result Verification
					</h1>
					<div class="mt-5 sm:flex align-centre sm:mt-10">
					  	<p class=" text-xs text-left text-gray-800 sm:text-center sm:text-xl">Enter the (UDID) reference number given in your SOR . </p>
							<!-- <a @click="showModal = true" class="text-blue-800 font-bold hover:text-blue-600">	see examples</a></p> -->
							
						
						
						</div>
						<Modal class="" />
					  <div class="mt-10 sm:mt-12">

						  <!-- This is a working waitlist form. Create your access key from https://web3forms.com/s to setup.  -->
						<form class="">
						  <div class="sm:flex">
							
							
							<div class="min-w-0 flex-1"><label for="udid"  class="sr-only">UDID </label>
								<input v-model="key" id="udid" type="text" placeholder="Enter your UDID" class="block w-full rounded-md border-0 bg-gray-200 px-4 py-3 text-base text-gray-900 placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-gray-400 data-input-student"  /></div>
							<div class="mt-3 sm:mt-0 sm:ml-3">
								<button @click="submitData()" type="button" class="block w-full rounded-md bg-indigo-900 py-3 px-4 font-medium text-white shadow hover:text-white focus:outline-none focus:ring-2 focus:ring-indigo-300 focus:ring-offset-2 focus:ring-offset-gray-900">Verify</button></div>
						  </div>
						</form>
						<div class="modal">
							<Transition>
								<ul class="mt-5 bg-gray-100 border-r border-b border-l border-t border-gray-200  bg-grey-400 rounded py-4 px-4 flex flex-col justify-between leading-normal" 
								v-if="!isHidden" >
									<li><span>Student username:<br></span><span class="font-bold text-indigo-900">{{studentFullname}}</span></li>
									<li><span>Exact Date and Time:<br></span><span class="font-bold text-indigo-900">{{studentDate}}</span></li>
									<li><span>PT Level:<br></span><span class="font-bold text-indigo-900">{{studentLevel}}</span></li>		
									
								</ul>
							</Transition>
							
							
						</div>

					  </div>
					</div>
					
				  </div>
				  
				  
				  
				</div>
			  </div>
			 
			  
		
			</div>
			
		  </div>
		  

		 
</template>

<script>

  import axios from "axios";
  import Modal from "@/components/Modal.vue";
  export default {
    name: "App",
	components: { Modal },
    data(){
      return {
       
		key: "",
		student: {},
		isHidden: true,
		//showModal: true
      }
    },
	computed: {
		studentFullname(){
			if(JSON.stringify(this.student) === '{}') {
				return ""
			}
			return this.student.fullname
		},
		studentDate(){
			if(JSON.stringify(this.student) === '{}') {
				return ""
			}
			return this.student.date_issued
		},
		studentLevel(){
			if(JSON.stringify(this.student) === '{}') {
				return ""
			}
			return this.student.pt_level
		}

	},
	methods: {
		
		submitData() {
			
				axios.get(`https://staging-etestapi.neostudyonline.com/sor/${this.key}/verify`)
      			.then((result) => {  
				this.student = result.data
				this.isHidden = false 
				})
				.catch((error) => {
				this.student = {}
				this.isHidden = true
				setTimeout(() => {
					 alert('use data not found')
				}, 500);
			}) 
			
		}
	}
    
  }
</script>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
