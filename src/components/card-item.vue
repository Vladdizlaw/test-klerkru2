<script setup>
import {ref} from 'vue'
const props = defineProps({
    preTitle: String,
    title: String,
    preContent: String,
    content1: String,
    content2: String,
    toggle: String,
    imgPath: URL,
    index: Number,
    isTurned:Boolean,
})

const emit = defineEmits(['update:isTurned'])

function HandleSwitcher(event){
    // console.log(event.target.checked)
    emit ('update:isTurned',{index:props.index, value:event.target.checked})
}
</script>
<template>
    <div class="w-[29rem] h-[13.5rem] bg-white rounded-md flex p-[1rem] relative h-fit " :class="{'drop-shadow-xl':props.isTurned}">
        <div class="flex lg:w-[79%] flex flex-col h-full w-full">
    
            <p class="text-sm text-gray-400 whitespace-nowrap ">{{ preTitle }}</p>
            <h1 class="text-xl whitespace-nowrap font-[600] pb-2">{{ title }}</h1>
            <p class="pb-2 text-sm textt-[#666666]">{{ preContent }}</p>
            <div class="flex items-center gap-1">
                <svg width="16" height="13" viewBox="0 0 16 13" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M5.08471 9.62365L1.93292 6.47186C1.57839 6.11733 1.00389 6.11631 0.648103 6.46959C0.290537 6.82464 0.289516 7.40265 0.645826 7.75896L5.08471 12.1978L15.3586 1.92397C15.7128 1.56972 15.7128 0.995371 15.3586 0.641122C15.0044 0.286991 14.4303 0.286855 14.076 0.640819L5.08471 9.62365Z"
                    fill="#00CC33" />
            </svg>
            <p class="font-[400] whitespace-nowrap text-sm">{{ content1 }}</p>
            </div>
            <div class="flex items-center pt-1 gap-1">
                <svg width="16" height="13" viewBox="0 0 16 13" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M5.08471 9.62365L1.93292 6.47186C1.57839 6.11733 1.00389 6.11631 0.648103 6.46959C0.290537 6.82464 0.289516 7.40265 0.645826 7.75896L5.08471 12.1978L15.3586 1.92397C15.7128 1.56972 15.7128 0.995371 15.3586 0.641122C15.0044 0.286991 14.4303 0.286855 14.076 0.640819L5.08471 9.62365Z"
                    fill="#00CC33" />
            </svg>
            <p class="font-[400] whitespace-nowrap text-sm ">{{ content2 }}</p>
            </div>
            <div class="w-full  flex items-center gap-2  pt-2">
        <label class="switch">
          <input type="checkbox" :checked="props.isTurned" @change="HandleSwitcher">
          <span class="slider round"></span>
        </label>
        <p>{{ toggle }}</p>
      </div>
        </div>
        <div class="absolute lg:relative lg:right-0 lg:top-10 right-5 top-5 lg:h-[20%] lg:w-auto h-[3rem] w-[3rem] flex items-end justify-end ">
              <img :src="imgPath"  alt=""/>
        </div>

    </div>
</template>
<style scoped>
.switch {
  position: relative;
  display: inline-block;
  width: 2.5rem;
  height: 1.21rem;
}


.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: .4s;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 18px;
  width: 20px;
  left: 1px;
  bottom: 1px;
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
}

input:checked+.slider {
  background-color: #2196F3;
}

input:focus+.slider {
  box-shadow: 0 0 1px #2196F3;
}

input:checked+.slider:before {
  -webkit-transform: translateX(14px);
  -ms-transform: translateX(14px);
  transform: translateX(18px);
}

.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>