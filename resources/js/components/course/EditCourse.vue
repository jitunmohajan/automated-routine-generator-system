<template>
    <main class="bg-white-500 flex-1 p-3 overflow-hidden">
        <div class="flex flex-col">
                        <!-- Card Sextion Starts Here -->
                        <div class="container mx-auto h-full flex flex-1 justify-center items-center">
                            <!--Horizontal form-->
                            <div class="mb-2 border-solid border-grey-light rounded border shadow-sm w-full md:w-1/2 lg:w-1/2">
                                <div class="bg-gray-300 px-2 py-3 border-solid border-gray-400 border-b">
                                   Update Course Information
                                </div>
                                <div class="p-3">
                                    <form class="w-full">
                                        <div class="md:flex md:items-center mb-6">
                                            <div class="md:w-1/4">
                                                <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                    for="inline-course-code">
                                                    Course Code
                                                </label>
                                            </div>
                                            <div class="md:w-3/4">
                                                <input class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                    id="inline-full-name" type="text" v-model="course.code">
                                            </div>
                                        </div>
                                        
                                        <div class="md:flex md:items-center mb-6">
                                            <div class="md:w-1/4">
                                                <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                    for="inline-course-code">
                                                    Course Name
                                                </label>
                                            </div>
                                            <div class="md:w-3/4">
                                                <input class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                    id="inline-full-name" type="text" v-model="course.name">
                                            </div>
                                        </div>
                                        
                                        
                                        <div class="md:flex md:items-center mb-6">
                                            <div class="md:w-1/4">
                                                <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                    for="inline-course-code">
                                                    Credit
                                                </label>
                                            </div>
                                            <div class="md:w-3/4 relative">
                                                <select class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                          v-model="course.credit"  id="grid-state">
                                                        <option value=1>1</option>
                                                        <option value=1.5>1.5</option>
                                                        <option value=2>2</option>
                                                        <option value=3>3</option>
                                                        <option value=4>4</option>
                                                        <option value=5>5</option>
                                                        <option value=6>6</option>
                                                    </select>
                                                    <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-grey-darker">
                                                        <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg"
                                                            viewBox="0 0 20 20">
                                                            <path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/>
                                                        </svg>
                                                    </div>
                                                    
                                            </div>
                                        </div>

                                        <div class="md:flex md:items-center mb-6">
                                            <div class="md:w-1/4">
                                                <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                    for="inline-course-code">
                                                    Course Type
                                                </label>
                                            </div>
                                            <div class="md:w-3/4 relative">
                                                
                                                <select class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                          v-model="course.type" id="grid-state">
                                                        <option value=0>Theory Class</option>
                                                        <option value=1>CSE LAB</option>
                                                        <option value=2>EEE LAB</option>
                                                        <option value=3>Communication LAB</option>
                                                        <option value=4>Mechanical LAB</option>
                                                        <option value=5>Physics LAB</option>
                                                    </select>
                                                    <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-grey-darker">
                                                        <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg"
                                                            viewBox="0 0 20 20">
                                                            <path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/>
                                                        </svg>
                                                    </div>
                                                    
                                            </div>
                                        </div>



                                        
                                        
                                        <div class="md:flex md:items-center">
                                            <div class="md:w-1/3"></div>
                                            <div class="md:w-2/3">
                                                <button @click.prevent="updateCourse" class="bg-green-500 hover:bg-green-800 text-white font-bold py-2 px-4 rounded-full">
                                                    Update Course 
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
          course: {}
        }
      },
      created() {
        let uri = `/api/course/edit/${this.$route.params.id}`;
        //console.log(this.$route.params.id);
         this.axios.get(uri).then((response) => {
             this.course = response.data.data; 
         });
      },
      methods: {
        updateCourse() {

            //console.log(this.course);
            let uri = `/api/course/update/${this.$route.params.id}`;
            this.axios.post(uri, this.course).then((response) => {
              this.$router.push({name: 'courses'});
            });
        },
        Cancel() {
            this.$router.go(-1);
        }
      }
    }
</script>
