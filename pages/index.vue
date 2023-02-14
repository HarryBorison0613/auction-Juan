<template>
  <div>
    <Header />
    <div class="bg-white border-b-[1px] border-[#e4e4e7] px-6">
      <div class="flex flex-wrap">
        <Filter :optionData="data1" placeholder="Property Type" />
        <Filter :optionData="data2" placeholder="Asset Type" />
        <Filter :optionData="data3" placeholder="Property Status" />
        <Filter :optionData="data4" placeholder="Occupancy" />
      </div>
    </div>
    <div class="flex flex-col">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 justify-center items-center gap-y-[20px] gap-x-[24px] px-[25px] py-[20px]">
        <ImageBox v-for="data in auctionData" :auctionData="data" />
      </div>
      <div class="flex w-full justify-center mt-4">

        <nav aria-label="Page navigation example">
          <ul class="inline-flex items-center -space-x-px">
            <li>
              <a href="#"
                class="block px-3 py-2 ml-0 leading-tight text-gray-500 bg-white border border-gray-300 rounded-l-lg hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">
                <span class="sr-only">Previous</span>
                <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                  xmlns="http://www.w3.org/2000/svg">
                  <path fill-rule="evenodd"
                    d="M12.707 5.293a1 1 0 010 1.414L9.414 10l3.293 3.293a1 1 0 01-1.414 1.414l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 0z"
                    clip-rule="evenodd"></path>
                </svg>
              </a>
            </li>
            <li>
              <a href="#"
                class="px-3 py-2 leading-tight text-gray-500 bg-white border border-gray-300 hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">1</a>
            </li>
            <li>
              <a href="#"
                class="px-3 py-2 leading-tight text-gray-500 bg-white border border-gray-300 hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">2</a>
            </li>
            <li>
              <a href="#" aria-current="page"
                class="z-10 px-3 py-2 leading-tight text-blue-600 border border-blue-300 bg-blue-50 hover:bg-blue-100 hover:text-blue-700 dark:border-gray-700 dark:bg-gray-700 dark:text-white">3</a>
            </li>
            <li>
              <a href="#"
                class="px-3 py-2 leading-tight text-gray-500 bg-white border border-gray-300 hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">4</a>
            </li>
            <li>
              <a href="#"
                class="px-3 py-2 leading-tight text-gray-500 bg-white border border-gray-300 hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">5</a>
            </li>
            <li>
              <a href="#"
                class="block px-3 py-2 leading-tight text-gray-500 bg-white border border-gray-300 rounded-r-lg hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">
                <span class="sr-only">Next</span>
                <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                  xmlns="http://www.w3.org/2000/svg">
                  <path fill-rule="evenodd"
                    d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z"
                    clip-rule="evenodd"></path>
                </svg>
              </a>
            </li>
          </ul>
        </nav>
      </div>
    </div>
    <div><button @click="getData">test</button></div>
    <Footer />
  </div>
</template>
<script>
import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';
import Filter from '@/components/Filter.vue';
import ImageBox from '@/components/ImageBox.vue';

export default {
  components: {
    Header,
    Footer,
    Filter,
    ImageBox
  },
  data() {
    return {
      data1: ['Multi Family', 'Single Family'],
      data2: ['Non-Bank Owned', 'Bank Owned'],
      data3: ['New to ListRE', 'Preview Properties'],
      data4: ['Occupied-No Interior Access', 'Vacant-Interior Access'],
      auctions: [],
      auctionData: [
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
        {
          name: 'Dennis Straussler',
          address: '780 Lynnway',
          state: 'Lynn, MA 1905',
          bed: 9,
          bath: 3,
          ft: 2388,
          cost: 714636
        },
      ]
    }
  },
  methods: {
    async getData() {
      await fetch('https://api.auctions.re/api:kjhCewq_/auctions')
        .then((res) => {
          console.log('res', res);
        })
    },
  },
}
</script>
