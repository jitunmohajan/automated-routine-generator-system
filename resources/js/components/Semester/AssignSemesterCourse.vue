<template>
 <main class="bg-white-500 flex-1 p-3 overflow-hidden">
        <div class="flex flex-col">
                        <!-- Card Sextion Starts Here -->
                        <div class="container mx-auto h-full flex flex-1 justify-center items-center">
                            <!--Horizontal form-->
                            <div class="mb-2 border-solid border-grey-light rounded border shadow-sm w-full md:w-1/2 lg:w-1/2">
                                <div class="bg-gray-300 px-2 py-3 border-solid border-gray-400 border-b">
                                 Assign Semester with course section
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
                                            <div class="md:w-3/4">
                                                <input class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                    id="inline-full-name" type="text" v-model="session_name" readonly>
                                            </div>
                                        </div>

                                        <div class="md:flex md:items-center mb-6">
                                            <div class="md:w-1/4">
                                                <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                    for="inline-course-code">
                                                    Semester
                                                </label>
                                            </div>
                                            <div class="md:w-3/4 relative">
                                                <select class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                      @click.prevent="SemesterSelect(assign_semester.semester)"   v-model="assign_semester.semester"    id="grid-state">
                                                        
                                                        <option disabled value="-1">Select Semester</option>
                                                        <option value="1">1st Semester</option>
                                                        <option value="2">2nd Semester</option>
                                                        <option value="3">3rd Semester</option>
                                                        <option value="4">4th Semester</option>
                                                        <option value="5">5th Semester</option>
                                                        <option value="6">6th Semester</option>
                                                        <option value="7">7th Semester</option>
                                                        <option value="8">8th Semester</option>
                                                        
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
                                                    Course
                                                </label>
                                            </div>
                                            <div class="md:w-3/4 relative">
                                                <select class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                        v-model="assign_semester.course_id" id="grid-state">
                                                        <option disabled value="-1">Select Course</option>
                                                        <option v-for="course in courses" :key="course.id " :value="course.id">{{course.name}}-{{course.code}}</option>
                                                        
                                                        
                                                    </select>
                                                    <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-grey-darker">
                                                        <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg"
                                                            viewBox="0 0 20 20">
                                                            <path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/>
                                                        </svg>
                                                    </div>
                                                    
                                            </div>
                                        </div>

                                        

                                <!-- ____________________number of section_____________________________ -->


                                        <div class="md:flex md:items-center mb-6">
                                            <div class="md:w-1/4">
                                                <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                    for="inline-course-code">
                                                    Number of Section
                                                </label>
                                            </div>
                                            <div class="md:w-3/4 relative">
                                                <select class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                          v-model="number_of_section" @change ="initializeSection" id="grid-state">
                                                        
                                                        <option disabled value=-1>Select Number of Section</option>
                                                        <option value=1>1</option>
                                                        <option value=2>2</option>
                                                        <option value=3>3</option>
                                                        <option value=4>4</option>
                                                        <option value=5>5</option>
                                                </select>
                                                <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-grey-darker">
                                                    <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg"
                                                         viewBox="0 0 20 20">
                                                        <path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/>
                                                    </svg>
                                                </div>
                                                    
                                            </div>
                                        </div>


                                        <div v-if="number_of_section>0" class="md:flex md:items-center mb-6">
                                            <div class="md:w-1/4">
                                                <label v-if="number_of_section>0"  class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                    for="inline-course-code">
                                                    Section
                                                </label>
                                            </div>
                                            <div class="md:w-3/4">
                                                <label v-if="number_of_section>0" class="inline-flex items-center">
                                                    <input v-model="assign_semester.section" type="checkbox"  value="A" class="form-checkbox" >
                                                    <span class="ml-2"> A</span>
                                                </label>
                                                
                                                <label v-if="number_of_section>0"  class="inline-flex items-center p-2">
                                                    
                                                </label>
                                            
                                                <label v-if="number_of_section>1" class="inline-flex items-center ">
                                                    <input v-model="assign_semester.section" type="checkbox"  value="B" class="form-checkbox" >
                                                    <span class="ml-2">  B</span>
                                                </label>
                                                <label v-if="number_of_section>1" class="inline-flex items-center p-2">
                                                    
                                                </label>

                                                <label v-if="number_of_section>2" class="inline-flex items-center">
                                                    <input v-model="assign_semester.section" type="checkbox"  value="C" class="form-checkbox" >
                                                    <span class="ml-2">  C</span>
                                                </label>
                                                <label v-if="number_of_section>2" class="inline-flex items-center p-2">
                                                    
                                                </label>
                                                
                                                <label v-if="number_of_section>3" class="inline-flex items-center">
                                                    <input v-model="assign_semester.section" type="checkbox"  value="D" class="form-checkbox" >
                                                    <span class="ml-2">  D</span>
                                                </label>
                                                <label v-if="number_of_section>3" class="inline-flex items-center p-2">
                                                    
                                                </label>
                                                
                                                <label v-if="number_of_section>4" class="inline-flex items-center">
                                                    <input v-model="assign_semester.section" type="checkbox"  value="E" class="form-checkbox" >
                                                    <span class="ml-2">  E</span>
                                                </label>
                                                 <label v-if="number_of_section>4" class="inline-flex items-center p-2">
                                                    
                                                </label>
<!-- _________________________________________________________________________________________________________________________ -->
                                                  <!-- <label v-if="number_of_section>1" class="inline-flex items-center">
                                                    <input type="checkbox" @click="checkAll()"  class="form-checkbox" >
                                                    <span class="ml-2">select all</span>
                                                </label>  -->

                                                <!-- <button v-if="number_of_section>0" @click.prevent="Reset" class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded-full">
                                                    Reset
                                                </button> -->
                                                    
                                            </div>
                                        </div>




                                        <div v-if="number_of_section>0 && checkCoursetype()" class="md:flex md:items-center mb-6">
                                            <div class="md:w-1/4">
                                                <label v-if="number_of_section>0"  class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                    for="inline-course-code">
                                                    Group
                                                </label>
                                            </div>
                                            <div class="md:w-3/4">
                                                <label v-if="number_of_section>0" class="inline-flex items-center">
                                                    <input v-model="group" type="checkbox"  value="A1" class="form-checkbox " >
                                                    <span class="ml-2"> A1</span>
                                                </label>
                                                
                                                <label v-if="number_of_section>0"  class="inline-flex items-center p-2">
                                                    
                                                </label>

                                                <label v-if="number_of_section>0" class="inline-flex items-center">
                                                    <input v-model="group" type="checkbox"  value="A2" class="form-checkbox" >
                                                    <span class="ml-2"> A2</span>
                                                </label>
                                                
                                                <label v-if="number_of_section>0"  class="inline-flex items-center p-2">
                                                    
                                                </label>
                                            
                                                <label v-if="number_of_section>1" class="inline-flex items-center ">
                                                    <input v-model="group" type="checkbox"  value="B1" class="form-checkbox" >
                                                    <span class="ml-2"> B1</span>
                                                </label>
                                                <label v-if="number_of_section>1" class="inline-flex items-center p-2">
                                                    
                                                </label>

                                                <label v-if="number_of_section>1" class="inline-flex items-center ">
                                                    <input v-model="group" type="checkbox"  value="B2" class="form-checkbox" >
                                                    <span class="ml-2"> B2</span>
                                                </label>
                                                <label v-if="number_of_section>1" class="inline-flex items-center p-2">
                                                    
                                                </label>

                                                <label v-if="number_of_section>2" class="inline-flex items-center">
                                                    <input v-model="group" type="checkbox"  value="C1" class="form-checkbox" >
                                                    <span class="ml-2">C1</span>
                                                </label>
                                                <label v-if="number_of_section>2" class="inline-flex items-center p-2">
                                                    
                                                </label>

                                                <label v-if="number_of_section>2" class="inline-flex items-center">
                                                    <input v-model="group" type="checkbox"  value="C2" class="form-checkbox" >
                                                    <span class="ml-2"> C2</span>
                                                </label>
                                                <label v-if="number_of_section>2" class="inline-flex items-center p-2">
                                                    
                                                </label>
                                                
                                                <label v-if="number_of_section>3" class="inline-flex items-center">
                                                    <input v-model="group" type="checkbox"  value="D1" class="form-checkbox" >
                                                    <span class="ml-2"> D1</span>
                                                </label>
                                                <label v-if="number_of_section>3" class="inline-flex items-center p-2">
                                                    
                                                </label>

                                                <label v-if="number_of_section>3" class="inline-flex items-center">
                                                    <input v-model="group" type="checkbox"  value="D2" class="form-checkbox" >
                                                    <span class="ml-2"> D2</span>
                                                </label>
                                                <label v-if="number_of_section>3" class="inline-flex items-center p-2">
                                                    
                                                </label>
                                                
                                                <label v-if="number_of_section>4" class="inline-flex items-center">
                                                    <input v-model="group" type="checkbox"  value="E1" class="form-checkbox" >
                                                    <span class="ml-2">  E1</span>
                                                </label>
                                                 <label v-if="number_of_section>4" class="inline-flex items-center p-2">
                                                    
                                                </label>

                                                <label v-if="number_of_section>4" class="inline-flex items-center">
                                                    <input v-model="group" type="checkbox"  value="E2" class="form-checkbox" >
                                                    <span class="ml-2">  E2</span>
                                                </label>
                                                 <label v-if="number_of_section>4" class="inline-flex items-center p-2">
                                                    
                                                </label>

                                                <!-- <button v-if="number_of_section>0" @click.prevent="Reset" class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded-full">
                                                    Reset
                                                </button> -->
                                                    
                                            </div>
                                        </div>





                                     
                                     
                                        
                                        <div class="md:flex md:items-center">
                                            <div class="md:w-1/3"></div>
                                            <div class="md:w-2/3">
                                                <button @click.prevent="assignSemester" class="bg-green-500 hover:bg-green-800 text-white font-bold py-2 px-4 rounded-full">
                                                    Assign Semester 
                                                </button>
                                            </div>

                                            <div class="md:w-2/3">
                                                <button @click.prevent="assignReturn" class="bg-blue-500 hover:bg-blue-800 text-white font-bold py-2 px-4 rounded-full">
                                                    Return to table 
                                                </button>
                                               <!-- <router-link tag="button"  class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-2 rounded-full" :to="{name: 'assigncourse', params: { id: selected_session }}" >Assign Semester with Course</router-link> -->
                                      
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

        data() {
            return {
                test:"",
                session_name:"",
                number_of_section:-1,
                session_id:0,
                course_id:0,
                courses:[],
                sessions:[],
                group:[],
                assign_semester:{
                    session_id:"",
                    semester:"-1",
                    course_id:"-1",
                    section:[],

                }
            
            }
        },
        created() {

            //this.assign_semester.session_name=this.$route.params.id;
            this.session_name=this.$route.params.id;

            let uri = '/api/courses';
            
            this.axios.get(uri).then((response) => {
                this.courses = response.data.data;
                
                //console.log(this.courses);
            });
            
            uri = '/api/sessions';
            
            this.axios.get(uri).then((response) => {
                this.sessions = response.data.data;
                
                //console.log(this.sessions);

                for(var i=0;i<this.sessions.length;i++){
                    if(this.sessions[i].session_name===this.session_name)
                        this.assign_semester.session_id=this.sessions[i].id;
                }
            });
        

            
        },

        methods:{
            SemesterSelect(semester){
                 console.log(semester);
                  if(semester>0){
                      let uri = `/api/courses/${semester}`;
            
                        this.axios.get(uri).then((response) => {
                            this.courses = response.data.data;
                            
                        console.log(this.courses);
                        });
                  }
            },
            initializeSection(){
                
                this.assign_semester.section = [];
                this.group = [];
                console.log(this.group);
                console.log(this.assign_semester.section);
                if(this.number_of_section == 1)
                {
                    this.assign_semester.section.push("A");
                    if(this.checkCoursetype())
                    {
                        this.group.push("A1");
                        this.group.push("A2");
                    }
                }
                else if(this.number_of_section == 2)
                {
                    this.assign_semester.section.push("A");
                    this.assign_semester.section.push("B");
                    if(this.checkCoursetype())
                    {
                        this.group.push("A1");
                        this.group.push("A2");
                        this.group.push("B1");
                        this.group.push("B2");
                    }
                }
                else if(this.number_of_section == 3)
                {
                    this.assign_semester.section.push("A");
                    this.assign_semester.section.push("B");
                    this.assign_semester.section.push("C");
                    if(this.checkCoursetype())
                    {
                        this.group.push("A1");
                        this.group.push("A2");
                        this.group.push("B1");
                        this.group.push("B2");
                        this.group.push("C1");
                        this.group.push("C2");
                    }
                }
                else if(this.number_of_section == 4)
                {
                    this.assign_semester.section.push("A");
                    this.assign_semester.section.push("B");
                    this.assign_semester.section.push("C");
                    this.assign_semester.section.push("D");
                    if(this.checkCoursetype())
                    {
                        this.group.push("A1");
                        this.group.push("A2");
                        this.group.push("B1");
                        this.group.push("B2");
                        this.group.push("C1");
                        this.group.push("C2");
                        this.group.push("D1");
                        this.group.push("D2");
                    }
                }
                else if(this.number_of_section == 5)
                {
                    this.assign_semester.section.push("A");
                    this.assign_semester.section.push("B");
                    this.assign_semester.section.push("C");
                    this.assign_semester.section.push("D");
                    this.assign_semester.section.push("E");
                    if(this.checkCoursetype())
                    {
                        this.group.push("A1");
                        this.group.push("A2");
                        this.group.push("B1");
                        this.group.push("B2");
                        this.group.push("C1");
                        this.group.push("C2");
                        this.group.push("D1");
                        this.group.push("D2");
                        this.group.push("E1");
                        this.group.push("E2");
                    }
                }
            },
            assignSemester(){
                console.log(this.assign_semester);
                for(var i = 0; i<this.number_of_section; i++)
                {
                    var flag = true;
                    for(var j=0; j<this.group.length; j++)
                    {
                        var temp = this.group[j];
                        if(this.assign_semester.section[i] == temp[0] )
                        {
                            flag = false;
                            break;
                        }
                    }
                    if(flag == true) this.group.push(this.assign_semester.section[i]);
                }
                this.assign_semester.section = [];
                this.assign_semester.section = this.group;
                console.log(this.assign_semester.section);
                let uri = '/api/semester-course/create';
                this.axios.post(uri, this.assign_semester).then((response) => {
                 //this.$router.push({name: 'sessions'});
                     console.log("Saved");
                     Swal.fire({
                    position: 'top-center',
                    icon: 'success',
                    title: 'Successfully Assigned',
                    showConfirmButton: false,
                    timer: 1500
                    })
                     
                      this.assign_semester.course_id="";
                      this.assign_semester.section=[];
                      this.number_of_section=0;
                    
                });

                  
            },
            assignReturn(){
               
                 this.$router.push({name: 'semestercourse', params: { session: this.session_name }});
        
                    
            },
            checkCoursetype(){
                for(var i=0;i<this.courses.length;i++){
                    if(this.courses[i].id==this.assign_semester.course_id && this.courses[i].type!=0)
                        return true;
                            

                 }
                 return false;
             },

            Reset(){
                this.number_of_section=0;
            },
            /*
            checkAll(){
                console.log(this.number_of_section);
               
                this.assign_semester.section[0]=="a";
                this.assign_semester.section[1]=="b";
                this.assign_semester.section[2]=="c";

               console.log(this.assign_semester.section);
                
                   for(var i=0;i<this.number_of_section;i++){
                        if(i==0)
                            this.assign_semester.section[i]="a";
                        else if(i==1)
                            this.assign_semester.section[i]="b";
                        else if(i==2)
                            this.assign_semester.section[i]="c";
                        else if(i==3)
                            this.assign_semester.section[i]="d";
                        else if(i==4)
                            this.assign_semester.section[i]="e";            
                    }
                    
            }
            */
        }

 


    }
</script>
