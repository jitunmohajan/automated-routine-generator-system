<template>
       <main class="bg-white-500 flex-1 p-3 overflow-hidden">

                <div class="flex flex-col">
                    <!-- Card Sextion Starts Here -->
                    <div class="container mx-auto h-full flex flex-1 justify-center items-center">
                        <!--Horizontal form-->
                        <div class="mb-2 border-solid border-grey-light rounded border shadow-sm w-full md:w-1/2 lg:w-1/2">
                            <div class="bg-gray-300 px-2 py-3 border-solid border-gray-400 border-b">
                                Update Teacher Information
                            </div>
                            <div class="p-3">
                                <form class="w-full">
                                    <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                User Name
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            <input class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                   id="inline-full-name" type="text" v-model="teacher.name">
                                        </div>
                                    </div>
                                     
                                    <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                Email
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            <input class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                   id="inline-full-name" type="text" v-model="teacher.email">
                                        </div>
                                    </div>
                                    
                                    
                                   

                                 



                                    <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                User Code
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            <input class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                   id="inline-full-name" type="text" v-model="teacher.code">
                                        </div>
                                    </div>


                                    
                                    
                                    <div class="md:flex md:items-center">
                                        <div class="md:w-1/3"></div>
                                        <div class="md:w-2/3">
                                            <button @click.prevent="updateUser" class="bg-green-500 hover:bg-green-800 text-white font-bold py-2 px-4 rounded-full">
                                                Update 
                                            </button>
                                        </div>
                                         <div class="md:w-2/3">
                                                 <button @click.prevent="Cancel" class="bg-red-500 hover:bg-red-800 text-white font-bold py-2 px-4 rounded-full">
                                                    Cancel 
                                                </button>
                                            </div> 
                                    </div>
                                </form>
                            </div>
                        </div>
                        <!--/Horizontal form-->

                       
                    </div>

                <!-- /Cards Section Ends Here -->

                   
                </div>
            </main>
</template>


<script>
    export default {

      data() {
        return {
          teacher: {}
        }
      },
      created() {

          
        let uri = `/api/teacher/edit/${this.$route.params.id}`;
        this.axios.get(uri).then((response) => {
            this.teacher = response.data.data; 
        });
      },
      methods: {
        updateUser() {

            console.log(this.teacher);
            let uri = `/api/teacher/update/${this.$route.params.id}`;
            this.axios.post(uri, this.teacher).then((response) => {
              this.$router.push({name: 'teachers'});
            });
        },
        Cancel() {
            this.$router.go(-1);
        }
      }
    }
</script>
