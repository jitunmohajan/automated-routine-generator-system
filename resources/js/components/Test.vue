<template>
        <main class="bg-white-500 flex-1 p-3 overflow-hidden">
        <div class="flex flex-1">
                        <!-- Card Sextion Starts Here -->
                        <div class="container mx-auto h-full flex flex-1 justify-center items-center">
                            <!--Horizontal form-->
                            <div class="mb-2 border-solid border-grey-light rounded border shadow-sm w-full md:w-1/2 lg:w-1/2">
                                <div class="bg-gray-300 px-2 py-3 border-solid border-gray-400 border-b">
                                    Select Session
                                </div>
                                <div class="p-3">
                                    <form class="w-full">
                                        <div class="md:flex md:items-center mb-6">
                                            <div class="md:w-1/4">
                                                <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                    for="inline-course-code">
                                                    Session Name
                                                </label>
                                            </div>
                                            <div class="md:w-3/4 relative">
                                                <select  class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                         @change="findSession" v-model="selected_session"  id="grid-state">
                                                        <option v-for="session in sessions" :key="session.id">{{session.session_name}}</option>
                                                       
                                                </select>
                                                <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-grey-darker">
                                                    <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg"
                                                         viewBox="0 0 20 20">
                                                        <path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/>
                                                    </svg>
                                                </div>
                                               
                                            </div>
                                        </div>
                                        
                                       <div class="md:flex md:items-center mb-6 justify-center space-x-2 ">
                                            
                                            <router-link tag="button" class=" bg-blue-900 hover:bg-blue-500 text-white font-bold py-2 px-2 rounded-full" :to="{name: 'createsession'}">Create Session</router-link>
                                            
                                            
                                             <router-link tag="button"  class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-2 rounded-full" :to="{name: 'assigncourse', params: { id: selected_session }}" >Assign Semester with Course</router-link>
                                             <router-link tag="button"  class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-2 rounded-full" :to="{name: 'semestercourse', params: { session: selected_session }}" >Semester with Course</router-link>
                                        </div>

                                            
                                            
                                        
                                        <!-- <div class="md:flex md:items-center"> -->
                                            
                                            
                                            <div class="md:flex md:items-center mb-6 justify-center space-x-2" >


                                                  

                                            
                                                    <button class="bg-orange-500 hover:bg-orange-800 text-white font-bold py-2 px-2 rounded-full" @click.prevent="generateRoutine" >Generate Routine</button>
                                                     <router-link tag="button" class="bg-blue-500 hover:bg-blue-800 text-white font-bold py-2 px-2 rounded-full" :to="{name: 'routine', params: { session: ses.id,day:day }}" >Show Routine</router-link>
                                                     <router-link tag="button" class="bg-blue-500 hover:bg-blue-800 text-white font-bold py-2 px-2 rounded-full" :to="{name: 'routine-information', params: { session: selected_session }}" >All course</router-link>
                                                    
                                            </div>
                                        <!-- </div> -->

                                       
                                        
                                    
                                        <div v-if="select_2==1" class="inset-0 top-0 pt-6">



                                                        <div class="md:flex md:items-center mb-6">
                                                        <div class="md:w-1/4">
                                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                                for="inline-course-code">
                                                                Select Day
                                                            </label>
                                                        </div>
                                                        <div class="md:w-3/4 relative">
                                                                <select v-model="day" class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                                        id="grid-state">
                                                                        <option value=-1>Select Day</option>
                                                                        <option value=1>Saturday</option>
                                                                        <option value=2>Sunday</option>
                                                                        <option value=3>Monday</option>
                                                                        <option value=4>Tuesday</option>
                                                                        <option value=5>Wednesday</option>
                                                                        <option value=6>Thursday</option>
                                                                    
                                                                    </select>
                                                                    <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-grey-darker">
                                                                        <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg"
                                                                            viewBox="0 0 20 20">
                                                                            <path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/>
                                                                        </svg>
                                                                    </div>
                                                            </div>
                                                        </div>
                                        
                                                        <div class="md:flex md:items-center mb-6 justify-center space-x-2">
                                                          <router-link tag="button" class="bg-blue-500 hover:bg-blue-800 text-white font-bold py-2 px-4 rounded-full" :to="{name: 'routine', params: { session: ses.id,day:day }}" >Show</router-link>
                                                       
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
import Swal from 'sweetalert2'
    export default {
        data(){
                return {
                selected_session:"",
                sessions:{
                        
                        session_name:"",
                        status:true
                },
                ses:[],
                select_2:0,
                day:1,
                
        
       
        
        
        }
        
    },
    created() {
        let uri = '/api/sessions';
        this.axios.get(uri).then(response => {
        this.sessions = response.data.data;
        console.log(this.sessions.length);
        this.checkSelectedSession();
        this.findSession();
        });
    },
    methods:{
        
        findSession(){
            console.log("found");
            let uri = `/api/find_session/${this.selected_session}`;
        this.axios.get(uri).then(response => {
        this.ses = response.data.data;
        console.log(this.ses);
        });
        },
        checkSelectedSession(){
          for(var i=0;i<this.sessions.length;i++)
          {
              if(this.sessions[i].status==1)
              {
                  this.selected_session=this.sessions[i].session_name;
                  //this.active_session=this.sessions[i].session_name;
              }
          }
        },
          generateRoutine(){
             let uri = `/api/generate-routine/${this.ses.id}`;
             console.log(uri);
            this.axios.get(uri).then(response => {
          		console.log("abc");
                Swal.fire(
                  'Success!',
                  'Successfully Generated!',
                  'success'
            )

		}).catch((e) => {
            Swal.fire({
                  type: 'error',
                  title: 'Oops...',
                  text: e.response.data
            })
          });
             
          },
          
          
          assignSelect(){
              this.select_2=1;
              //cosole.log(this.day);
          }
     
      }
   
  }
</script>

