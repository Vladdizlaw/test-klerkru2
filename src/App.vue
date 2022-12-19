<script setup>
import CardItem from "@/components/card-item.vue"
import { reactive, onMounted, onBeforeUnmount, computed } from 'vue'
const state = reactive({
  screenWidth: window.innerWidth
})
const cardContent = reactive([
  {
    preTitle: 'Перед рассветом',
    title: 'Утренний бухгалтер',
    preContent: 'Самые важные новости и события за день. Кратко, по делу, структурировано.',
    content1: 'Новости для бухгалтеров, ИП и директора',
    content2: 'Подборка статей за день',
    toggle: 'Уже получает 59 342 человек',
    imgPath: new URL('./assets/card1.svg', import.meta.url),
    isTurned: false
  },
  {
    preTitle: 'После заката',
    title: 'Ночной бухгалтер',
    preContent: 'Самая краткая газета о налогах и бухучете в мире — современная рассылка для чтения.',
    content1: 'Анализ, оценка и только самое главное',
    content2: 'Лучшие комменты юзеров в обзоре',
    toggle: 'Уже получает 37 480 человек',
    imgPath: new URL('./assets/card2.svg', import.meta.url),
    isTurned: false
  },
  {
    preTitle: 'Раз в две недели',
    title: 'Ножницы скидок',
    preContent: 'Подборка самых выгодных и полезных спецпредложений от надежных компаний.',
    content1: 'Акции и скидки от лидеров рынка',
    content2: 'Те, кто подписался – экономят много денег ',
    toggle: 'Уже получает 92 118 человек',
    imgPath: new URL('./assets/card3.svg', import.meta.url),
    isTurned: false
  },
  {
    preTitle: 'По мере появления анонсов',
    title: 'Чемодан вебинаров',
    preContent: 'Подборка с анонсами бесплатных вебинаров на самые топовые темы при участии экспертов.',
    content1: 'Никогда не пришлем платные вебинары',
    content2: 'Подборка топовых тем для вебинаров',
    toggle: 'Уже получает 92 082 человек',
    imgPath: new URL('./assets/card4.svg', import.meta.url),
    isTurned: false
  },
])


const isAllSwitchersTurned = computed(() => {
  return cardContent.every(el => el.isTurned)
})
function turnOnAllSwitchers(event) {
  cardContent.forEach((el, i) => {
    cardContent[i].isTurned = event.target.checked
  })
}
function resizeScreen(ev) {
  state.screenWidth = ev.currentTarget.innerWidth
}
onMounted(() => {
  window.addEventListener("resize", resizeScreen)
})
onBeforeUnmount(() => {
  window.removeEventListener("resize", resizeScreen)
})
</script>

<template>
  <div class="w-full lg:h-screen flex flex-col justify-start items-center pt-[2rem]">

    <div class="w-full flex justify-center pb-[1rem]">
      <svg width="76" height="36" viewBox="0 0 76 36" fill="none" xmlns="http://www.w3.org/2000/svg">
        <g clip-path="url(#clip0_1_2463)">
          <path
            d="M73.1422 11C73.1422 14.21 70.1549 17 67.1716 17V11L65.1814 11.0001V25H67.1716V19C70.1569 19 73.1422 21.7912 73.1422 25H75.1324C75.1324 21.0598 73.1422 19 70.3847 18C73.1422 17 75.1324 14.5085 75.1324 11H73.1422ZM8.46078 11C8.46078 14.21 5.47355 17 2.4902 17V11L0.5 11.0001V25H2.4902V19C5.47549 19 8.46078 21.7912 8.46078 25H10.451C10.451 21.0598 8.46078 19 5.70337 18C8.46078 17 10.451 14.5085 10.451 11H8.46078ZM16.6446 12.9536C16.6308 12.9914 12.4412 24.5732 12.4412 24.5732L14.6481 25.36C14.6481 25.36 18.8779 13.6631 18.8825 13.6463C18.9902 13.3232 19.2934 13.3266 19.3932 13.3278C19.5951 13.327 19.8358 13.388 19.9425 13.6831L24.1656 25.36L26.3725 24.5732L22.1688 12.9525C21.9409 12.2484 21.1009 11.0013 19.4187 11.0002C17.6879 10.9868 16.868 12.2236 16.6446 12.9536ZM50.2549 18C50.2549 15.2429 52.4868 13 55.2304 13C57.9739 13 60.2059 15.2429 60.2059 18C60.2059 20.7571 57.9739 23 55.2304 23C52.4868 23 50.2549 20.7571 50.2549 18ZM48.2647 18V34H50.2549V22.51C51.1334 24.0506 53.4758 24.9666 55.2304 25C59.13 24.9666 62.2717 21.8339 62.1961 18C62.2717 14.1327 59.13 11 55.2304 11C51.4065 11 48.2647 14.1327 48.2647 18Z"
            fill="black" />
          <path
            d="M44.0442 20.2256L45.5914 21.4214C45.5835 21.432 44.725 22.5291 43.6493 24.6541C42.3339 27.2505 41.7593 28.6841 41.7534 28.6976L41.7131 28.7868C39.7612 32.5345 36.6128 34.2153 33.2905 33.2842C31.5223 32.7876 30.0567 31.6432 29.1627 30.0603C28.2688 28.4764 28.0527 26.6434 28.5547 24.8985L33.1039 9.05904C33.5066 7.6585 34.4379 6.49656 35.7248 5.78757C37.0126 5.07857 38.5028 4.90787 39.9223 5.30553C42.8497 6.12703 44.555 9.1473 43.724 12.0376L43.7171 12.0589L40.2661 23.0751L40.272 23.0537C39.6463 25.2292 37.4586 26.4572 35.2915 25.8499C34.2503 25.558 33.3976 24.9015 32.8897 24.0013C32.371 23.0829 32.2532 21.9926 32.5597 20.9277L35.711 10.1754L37.5981 10.7147L34.4477 21.4622C34.2866 22.0247 34.3426 22.5901 34.6059 23.0566C34.8623 23.5105 35.2847 23.8316 35.8279 23.984C36.9537 24.2992 38.0519 23.6715 38.382 22.5242L38.3889 22.5018C38.3889 22.5018 41.8221 11.5429 41.8339 11.5051C41.9253 11.187 41.9695 10.866 41.9695 10.5498C41.9695 9.02024 40.9479 7.61001 39.385 7.17161C38.4704 6.91556 37.5107 7.02516 36.6816 7.48198C35.8534 7.93783 35.2532 8.6866 34.9939 9.5886L30.4447 25.428C29.705 28.0002 31.2227 30.6868 33.8279 31.4181C37.1904 32.3609 39.216 29.3251 39.9469 27.9352C40.0618 27.654 40.6541 26.2312 41.8919 23.787C43.0668 21.4679 44.0049 20.275 44.0442 20.2256Z"
            fill="#EF3124" />
        </g>
        <defs>
          <clipPath id="clip0_1_2463">
            <rect width="75" height="36" fill="white" transform="translate(0.5)" />
          </clipPath>
        </defs>
      </svg>
    </div>
    <div class="w-full flex  flex-row iems-center justify-center gap-2 lg:pb-[1.5rem] ">
      <a class="text-sm text-gray-400 whitespace-nowrap hover:underline cursor-pointer">Главная</a>
      <p class="text-sm text-gray-400">&#8594 </p>
      <a class="text-sm text-gray-400 whitespace-nowrap hover:underline cursor-pointer">Рассылки</a>
      <p class="text-sm text-gray-400">&#8594 </p>
      <a class="text-sm text-gray-400 whitespace-nowrap hover:underline cursor-pointer">Хлебные крошки </a>
    </div>
    <h4 class="lg:text-5xl font-[600] md:text-4xl pb-[1.5rem] text-[2.1rem] ">Подписки «Клерка»</h4>
    <div class="flex lg:justify-center justify-around w-[90%] lg:w-auto items-center gap-6 relative">
      <a class="text-sm text-[#5A8CF1]" href="">Рассылки</a>
      <a class="text-sm text-[#666666] " href="">Соцсети</a>
      <a class="text-sm text-[#666666]" href="">Мессенджеры</a>
      <div class="h-[2px] w-[3.8rem] bg-[#5A8CF1] absolute left-5 lg:left-0 bottom-[-15px]"></div>
    </div>
    <div
      class=" mt-[1rem] lg:w-[65%] lg:max-w-[61rem] h-[100%] w-full lg:h-fit bg-[#F5F5F8] flex flex-col justify-start items-center rounded-lg flex flex-col p-[1rem] pb-[3rem] ">
      <h1 class="text-2xl font-[600] pt-[1rem]">Выберите рассылки, которые подходят именно вам</h1>
      <div class="w-full flex justify-center pt-[1rem] xl:px-[2rem]">
        <input type="text" class="w-[100%] rounded-md h-[3rem] p-[1rem] relative" placeholder="Электронная почта" />
        <button
          class="absolute lg:right-[1.7rem] md:right-[0px] top-50 lg:py-[0.8rem] lg:px-[1.5rem] md:py-[0.5rem] md:px-[1rem] p-[1rem]  lg:rounded-3xl rounded-full right-[-5px] bg-[#316FEE] flex justify-center items-center text-white">
          <p v-if="state.screenWidth > 500">Подписаться</p><svg v-if="state.screenWidth < 500" width="14" height="14"
            viewBox="0 0 9 14" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M0.349976 12.355L5.69331 7L0.349976 1.645L1.99498 0L8.99498 7L1.99498 14L0.349976 12.355Z"
              fill="white" />
          </svg>
        </button>

      </div>
      <div class="w-full pt-[1rem] flex items-center gap-2  lg:px-[2rem]">
        <label class="switch">
          <input type="checkbox" v-model="isAllSwitchersTurned" @change="turnOnAllSwitchers">
          <span class="slider round"></span>
        </label>
        <p>Подписаться на все рассылки</p>
      </div>
      <div class="flex w-full  h-full pt-[2rem] flex-row flex-wrap lg:justify-between gap-[1rem]">
        <CardItem v-for="item, index in cardContent" :key="index" :preTitle="item.preTitle" :title="item.title"
          :preContent="item.preContent" :content1="item.content1" :content2="item.content2" :toggle="item.toggle"
          :imgPath="item.imgPath" :isTurned="item.isTurned" :index="index"
          @update:isTurned="cardContent[$event.index].isTurned = $event.value" />
      </div>


    </div>

    <div class="w-full h-full flex justify-center items-center py-[2rem] ">
      <svg width="196" height="48" viewBox="0 0 196 48" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M16.0993 7.74633H0.93335V4.49787H16.0993V7.74633Z" fill="black" />
        <path d="M19.8005 4.24799H23.7726L37.4942 40.1628H33.5221L19.8005 4.24799Z" fill="black" />
        <path d="M58.6182 40.7534H37.9455V37.3232H58.6182V40.7534Z" fill="black" />
        <path
          d="M61.71 23.8978C61.71 20.4752 62.1614 17.1888 63.0641 14.0388C63.9819 10.8888 65.3436 8.0265 67.149 5.45196C68.9545 2.87743 70.8277 1.0601 72.7686 0L73.6262 2.77142C71.4295 4.46758 69.624 7.05726 68.2097 10.5405C66.8105 14.0237 66.0432 17.9233 65.9078 22.2395L65.8852 24.1704C65.8852 30.0161 66.9459 35.0894 69.0673 39.3904C70.3462 41.965 71.8658 43.9792 73.6262 45.433L72.7686 48C70.7675 46.8793 68.8567 45.0014 67.0362 42.3663C63.4854 37.2172 61.71 31.0611 61.71 23.8978Z"
          fill="black" />
        <path
          d="M95.5827 2.33762L92.0237 3.54723C93.1792 5.96645 95.8138 13.1776 96.5533 15.8294L100.158 14.5733C99.3727 11.968 96.5995 4.57074 95.5827 2.33762ZM116.104 5.31512L111.852 4.10551C110.928 11.084 108.108 18.5278 104.457 23.2266C99.7887 29.1816 92.9019 33.6479 86.2924 35.6019L89.4816 38.8585C95.9986 36.5323 102.839 31.7404 107.6 25.4132C111.39 20.3887 113.886 13.7359 115.272 7.96695C115.457 7.22258 115.781 6.10602 116.104 5.31512ZM82.6873 5.12902L79.0359 6.4782C80.1452 8.47871 83.3344 16.3412 84.2125 19.2256L87.8639 17.8764C86.8009 14.8524 83.889 7.73434 82.6873 5.12902Z"
          fill="black" />
        <path
          d="M133.523 24.1249C133.523 27.5021 133.079 30.743 132.191 33.8476C131.318 36.9371 129.972 39.7918 128.151 42.4117C126.346 45.0317 124.45 46.8945 122.464 48L121.584 45.433C123.901 43.646 125.759 40.8746 127.158 37.1188C128.573 33.3478 129.295 29.168 129.325 24.5793V23.8523C129.325 20.672 128.994 17.7189 128.332 14.9929C127.67 12.2518 126.745 9.79839 125.556 7.63275C124.382 5.46711 123.058 3.77851 121.584 2.56697L122.464 0C124.45 1.10554 126.338 2.95315 128.129 5.54283C129.934 8.13251 131.281 10.9872 132.169 14.107C133.071 17.2267 133.523 20.566 133.523 24.1249Z"
          fill="black" />
        <path d="M157.558 40.7534H136.885V37.3232H157.558V40.7534Z" fill="black" />
        <path d="M161.643 40.1628H158.055L171.776 4.24799H175.342L161.643 40.1628Z" fill="black" />
        <path d="M195.067 7.74633H179.901V4.49787H195.067V7.74633Z" fill="black" />
      </svg>
    </div>

  </div>

</template>
 
<style scoped>
.switch {
  position: relative;
  display: inline-block;
  width: 2rem;
  height: 1rem;
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
  height: 15px;
  width: 16px;
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
  transform: translateX(14px);
}

.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>