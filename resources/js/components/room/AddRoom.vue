<template>
       <main class="bg-white-500 flex-1 p-3 overflow-hidden">

                <div class="flex flex-col">
                    <!-- Card Sextion Starts Here -->
                    <div class="container mx-auto h-full flex flex-1 justify-center items-center">
                        <!--Horizontal form-->
                        <div class="mb-2 border-solid border-grey-light rounded border shadow-sm w-full md:w-1/2 lg:w-1/2">
                            <div class="bg-gray-300 px-2 py-3 border-solid border-gray-400 border-b">
                                Room Information
                            </div>
                            <div class="p-3">
                                <form class="w-full">
                                    <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                Room Number
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            <input class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                   id="inline-full-name" type="number" v-model="room.number" placeholder="Enter Room Number">
                                        </div>
                                    </div>
                                     
                                    <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                Room Name
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            <input class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                   id="inline-full-name" type="text" v-model="room.name" placeholder="Enter Room Name">
                                        </div>
                                    </div>
                                    
                                    
                                   

                                    <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                Room Type
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            
                                            <select class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                       v-model="room.type" id="grid-state">
                                                    <option disabled value="-1">Select Course Type</option>
                                                    <option value="0">Theory Class</option>
                                                    <option value="1">CSE LAB</option>
                                                    <option value="2">EEE LAB</option>
                                                    <option value="3">Communication LAB</option>
                                                    <option value="4">Mechanical LAB</option>
                                                    <option value="5">Physics LAB</option>
                                                </select>
                                                
                                        </div>
                                    </div>


                                   



                                    <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                Capacity
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            <input class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                   id="inline-full-name" type="number" v-model="room.capacity" placeholder="Enter Capacity">
                                        </div>
                                    </div>



                                   <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                           
                                        </div>
                                        <div class="md:w-3/4">
                                            <input type="checkbox"   :value=1 v-model="room.entry_type">Set Room Schedule
                                        </div>
                                    </div>  
                                 

                                <section v-if="room.entry_type==1">
                                     <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                Day 
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            
                                            <select class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                       v-model="day" id="grid-state">
                                                <option disabled value="-1">Select Day</option>
                                                <option value=0>Saturday</option>
                                                <option value=1>Sunday</option>
                                                <option value=2>Monday</option>
                                                <option value=3>Tuesday</option>
                                                <option value=4>Wednesday</option>
                                                </select>
                                                
                                        </div>
                                    </div>

                                    <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                Time Start
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            
                                            <select class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                       v-model="time1" id="grid-state">
                                                <option disabled value="-1">Select Start Time</option>
                                                <option value=1>8.30 AM</option>
                                                <option value=2>9.00 AM</option>
                                                <option value=3>9.30 AM</option>
                                                <option value=4>10.00 AM</option>
                                                <option value=5>10.30 AM</option>
                                                <option value=6>11.00 AM</option>
                                                <option value=7>11.30 AM</option>
                                                <option value=8>12.00 PM</option>
                                                <option value=9>12.30 PM</option>
                                                <option value=10>1.00 PM</option>
                                                <option value=11>1.30 PM</option>
                                                <option value=12>2.00 PM</option>
                                                <option value=13>2.30 PM</option>
                                                <option value=14>3.00 PM</option>
                                                <option value=15>3.30 PM</option>
                                                <option value=16>4.00 PM</option>
                                                <option value=17>4.30 PM</option>
                                                <option value=18>5.00 PM</option>
                                                <option value=19>5.30 PM</option>
                                                </select>
                                                
                                        </div>
                                    </div>


                                     <div class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                Time End
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                            
                                            <select class="block appearance-none w-full bg-grey-200 border border-grey-200 text-grey-darker py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-grey"
                                                @change="SetTime()" v-model="time2" id="grid-state">
                                                <option disabled value="-1">Select End Time</option>
                                                <option value=1>8.30 AM</option>
                                                <option value=2>9.00 AM</option>
                                                <option value=3>9.30 AM</option>
                                                <option value=4>10.00 AM</option>
                                                <option value=5>10.30 AM</option>
                                                <option value=6>11.00 AM</option>
                                                <option value=7>11.30 AM</option>
                                                <option value=8>12.00 PM</option>
                                                <option value=9>12.30 PM</option>
                                                <option value=10>1.00 PM</option>
                                                <option value=11>1.30 PM</option>
                                                <option value=12>2.00 PM</option>
                                                <option value=13>2.30 PM</option>
                                                <option value=14>3.00 PM</option>
                                                <option value=15>3.30 PM</option>
                                                <option value=16>4.00 PM</option>
                                                <option value=17>4.30 PM</option>
                                                <option value=18>5.00 PM</option>
                                                <option value=19>5.30 PM</option>
                                                </select>
                                                
                                        </div>
                                    </div>

                                   
                                   <div v-if="day!=-1" class="md:flex md:items-center mb-6">
                                        <div class="md:w-1/4">
                                            <label class="block text-gray-500 font-regular md:text-right mb-1 md:mb-0 pr-4"
                                                   for="inline-course-code">
                                                Day wise Time
                                            </label>
                                        </div>
                                        <div class="md:w-3/4">
                                           
                                            
                                            <div>
                                                <input type="checkbox"   :value=1 v-model="room.duration[day][0]"> 08.30 - 09.00 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                                <input type="checkbox"  :value=1 v-model="room.duration[day][1]"> 09.00 - 09.30 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                                <input type="checkbox"  :value=1 v-model="room.duration[day][2]"> 09.30 - 10.00
                                           </div>
                                           <div>
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][3]"> 10.00 - 10.30 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][4]"> 10.30 - 11.00 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][5]"> 11.00 - 11.30
                                           </div>
                                           <div>
                                            <input type="checkbox"  :value=1 v-model="room.duration[day][6]"> 11.30 - 12.00 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                            <input type="checkbox"  :value=1 v-model="room.duration[day][7]"> 12.00 - 12.30 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                            <input type="checkbox"  :value=1 v-model="room.duration[day][8]"> 12.30 - 01.00
                                                </div>
                                                <div>
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][9]"> 01.00 - 01.30 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][10]"> 01.30 - 02.00 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][11]"> 02.00 - 02.30
                                                </div>
                                                <div>
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][12]"> 02.30 - 03.00 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][13]"> 03.00 - 03.30 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][14]"> 03.30 - 04.00
                                                </div>
                                                <div>
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][15]"> 04.00 - 04.30 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][16]"> 04.30 - 05.00 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                                           <input type="checkbox"  :value=1 v-model="room.duration[day][17]"> 05.00 - 05.30
                                                </div>
                                                
                                        </div>
                                    </div> 


                                  
                                </section>




                                    
                                    
                                    <div class="md:flex md:items-center">
                                        <div class="md:w-1/3"></div>
                                        <div class="md:w-2/3">
                                            <button @click.prevent="addRoom" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded-full">
                                                Save Room 
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
        data(){
        return {
          day:-1,
          time1:-1,
          time2:-1,
          duration:0,
          room:{
              entry_type:0,
              number:0,
              name:"",
              type:-1,
              capacity:0,
              free_time:"",
              status:false,
              duration:[]
          }
        }
    },
    created(){
        for(var i=0;i<5;i++){ 
            this.room.duration[i]=[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,];
        }
    },
    methods: {
       SetCheck(i,j){
            if(this.room.duration[i][j]==true){
                this.room.duration[i][j]=1;
            }
            else if(this.room.duration[i][j]==false){
                this.room.duration[i][j]=0;
            }
            else{
                this.room.duration[i][j]=this.duration[i][j];
            }
       },

      SetTime(){
       
           if(this.time1>-1 && this.time2>-1){
               for(var i=this.time1-1;i<this.time2-1;i++){
                    this.room.duration[this.day][i]=1;
               
                }
                
                this.time1=-1;
                this.time2=-1;
                    console.log(this.room.duration);
           }
           
           
      },
      addRoom(){

        if(this.room.entry_type!=1)
        {
            var temp="";
            for(var i=0; i<90; i++)
            {
                temp+="0";
            }
            console.log(temp.length);
            this.room.free_time = temp;
        }
        else
        {
            var temp="";
            for(var i=0;i<5;i++){ 
                
                for(var j =0 ; j<this.room.duration[i].length; j++){
                if(this.room.duration[i][j] != 0){
                    temp+="0";
                }
                else
                {
                    temp+="1";
                }
                }
            }
            console.log(temp);
            console.log(temp.length);
            this.room.free_time = temp;
        }
        console.log(this.room);
        
           let uri = '/api/room/create';
          this.axios.post(uri, this.room).then((response) => {
          this.$router.push({name: 'rooms'});
       });
}
    }
  }
</script>