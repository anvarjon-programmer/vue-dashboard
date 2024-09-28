<template>
    <div class="w-screen h-screen flex">
       <div class="w-[400px] h-full bg-gray-200 text-white" v-show="showSide">
          <div class="h-[50px] bg-gray-300 flex items-center justify-center">
            <div class="px-[20px]">
                <h3 class="font-bold text-xl">Admin Dashboard</h3>
            </div>
          </div>
          <div class="h-[calc(100vh-50px)] bg-gray-800 py-[20px]">
            <div class="flex flex-col justify-between h-full px-[20px] space-y-[10px]">
                <div class=" flex flex-col justify-between  space-y-[10px]">
                <div v-for="(item,index) in data" :key="index">
                 <router-link :to="item.path" class="inline-flex relative items-center py-[10px] px-[10px] w-full text-sm font-medium rounded-md border-gray-200 hover:bg-gray-300 hover:text-white">
                     {{ item.name }}
                 </router-link>
                </div>
                </div>
            <div class="h-[50px]">
                <div>
                    <router-link to="/setting" class="inline-flex relative items-center py-[10px] px-[10px] w-full text-sm font-medium rounded-md border-gray-200 hover:bg-gray-300 hover:text-white">
                        Settings
                    </router-link>
                </div>
            </div>
            </div>
            
          </div>
        </div>
        <div class="w-full h-full bg-gray-400">
            <div class="h-[50px] bg-gray-100 flex items-center shadow-sm px-[20px] w-full py-[10px] z-10 border-b">
             <div class="cursor-pointer w-[30px]" @click="toggleSidebar">
                open
             </div>


             <div class="w-[calc(100%-30px)] flex">
                <div class="w-[calc(100%-200px)] flex justify-center">
                    <form class="flex items-center w-[500px]">
                        <label for="voice-search" class="sr-only">Search</label>
                        <div class="relative w-full">
                            <div class="flex absolute inset-y-0 left-0 items-center pl-3 pointer-events-none">
                                <!-- searcj icons -->s
                            </div>
                            <input type="text" id="voice-search" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue">
                            <router-link to="/" class="flex absolute inset-y-0 right-0 items-center pr-3">G</router-link>
                        </div>
                    </form>
                </div>
                <div class="w-[200px]">
                    <div class="flex items-center justify-center space-y-4" @click="toggleDrop">
                        <div>H</div>
                        <div class="font-semibold dark:text-white text-left">
                            <div>Madona, Dev Op</div>
                              <div class="text-xs text-gray-500 dark:text-gray-400">Admin</div>
                        </div>
                    </div>
                    <div v-show="showDropDown" class="absolute right-[18px] z-18 mt-2 w-56 origin-top-right rounded-md bg-white shadow-lg ring-1">
                        <div class="py-1 text-left" role="none">
                            <a href="#">1</a>
                            <a href="#">1</a>
                            <a href="#">1</a>
                            <form type="submit">add</form>
                        </div>
                    </div>
                </div>
             </div>
          </div>
          <div class="h-[calc(100vh-50px)] bg-gray-50 p-[20px]">
            <div class="border border-gray-300 rounded-md p-[20px] h-full">
                <router-view></router-view>
            </div>
          </div>
        </div>
    </div>
</template>
<script>
import { data } from '@/constants/BarLinks';


export default {
    data(){
        return{
            data,
            showDropDown:false,
            showSide:true
            
        }
    },
    methods:{
        toggleSidebar(){
            this.showSide = !this.showSide
        },
        toggleDrop(){
            this.showDropDown = !this.showDropDown
        }
    }
}
</script>
<style>
    
</style>