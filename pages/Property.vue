<template>
    <div>
        <Header />
        <div class="py-20px px-[10%]">
            <div class="flex flex-wrap justify-start items-stretch pt-[18px] px-[16px]">
                <div class="flex justify-start items-center">
                    <div class="mr-[5px] text-[#118bf4] text-[21px] p-0">
                        <svg class="w-4 h-4 font-bold" fill="currentColor" viewBox="0 0 20 20"
                            xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
                            <path clip-rule="evenodd" fill-rule="evenodd"
                                d="M12.79 5.23a.75.75 0 01-.02 1.06L8.832 10l3.938 3.71a.75.75 0 11-1.04 1.08l-4.5-4.25a.75.75 0 010-1.08l4.5-4.25a.75.75 0 011.06.02z">
                            </path>
                        </svg>
                    </div>
                    <p class="p-0 text-[16px] font-semibold text-left text-[#118bf4]">
                        Back to Listings
                    </p>
                </div>
            </div>
            <div class="p-[8px] relative">
                <div class="grid grid-row md:grid-cols-3">
                    <div class="md:col-span-2">
                        <div class="flex flex-col p-2 justify-start items-stretch">
                            <Carousel :urls="urls" />
                            <div class="flex mt-[32px] ">
                                <div class="rounded-[6px] bg-gradient-to-r from-cyan-500 to-blue-500">
                                    <p class="py-[5px] px-[10px] text-[16px] text-white">
                                        Land
                                    </p>
                                </div>
                            </div>
                            <div class="mt-[5px] md:grid md:grid-row md:grid-cols-2">
                                <div class="md:col-span-1">
                                    <div class="flex-col">
                                        <h3 class="text-[32px] font-[600]">1775 Washington St</h3>
                                        <p class="text-[22px]">
                                            Hanover, MA 2339
                                        </p>
                                    </div>
                                </div>
                                <div class="md:col-span-1">
                                    <div class="flex flex-wrap md:justify-end gap-x-[46px] p-[8px]">
                                        <div class="flex-col justify-center items-center order-1">
                                            <p class="text-[28px] font-[600]">
                                                4
                                            </p>
                                            <p class="text-[18px]">
                                                Beds
                                            </p>
                                        </div>
                                        <div class="flex-col justify-center items-center order-1">
                                            <p class="text-[28px] font-[600]">
                                                3
                                            </p>
                                            <p class="text-[18px]">
                                                Baths
                                            </p>
                                        </div>
                                        <div class="flex flex-col flex-nowrap justify-center items-center order-2">
                                            <p class="text-[28px] font-[600]">
                                                7,140
                                            </p>
                                            <p class="text-[18px]">
                                                Square Feet
                                            </p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="mt-[12px] flex">
                                <div class="w-[200px] flex flex-wrap">
                                    <div class="mr-[9px] flex justify-center items-center">
                                        <svg class="w-4 h-4 fill-blue-500" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--! Font Awesome Pro 6.2.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path d="M498.1 5.6c10.1 7 15.4 19.1 13.5 31.2l-64 416c-1.5 9.7-7.4 18.2-16 23s-18.9 5.4-28 1.6L284 427.7l-68.5 74.1c-8.9 9.7-22.9 12.9-35.2 8.1S160 493.2 160 480V396.4c0-4 1.5-7.8 4.2-10.7L331.8 202.8c5.8-6.3 5.6-16-.4-22s-15.7-6.4-22-.7L106 360.8 17.7 316.6C7.1 311.3 .3 300.7 0 288.9s5.9-22.8 16.1-28.7l448-256c10.7-6.1 23.9-5.5 34 1.4z"/></svg>
                                    </div>
                                    <a href="https://www.google.com/maps/dir//1775 Washington St Hanover, MA 2339">
                                        <p class="text-[16px] font-[600] text-blue-500">
                                            Get Directions
                                        </p>
                                    </a>
                                </div>
                            </div>
                            <div class="mt-[30px] flex-col">
                                <h4 class="text-[20px] font-[600]">Description</h4>
                                <p class="pt-[5px] text-[16px]">
                                    This is a beautiful home you will really like it.
                                </p>
                            </div>
                            <div class="mt-[56px] flex-col">
                                <h4 class="text-[20px] font-[600] mb-[10px]">Bid History</h4>
                                <div class="flex flex-col">
                                    <div class="px-[8px] grid grid-row grid-cols-3 bg-[#edf2f9]">
                                        <div class="col-span-1">
                                            <p class="text-[12px] p-[16px] font-[500] text-[#95aac9]">BIDDER</p>
                                        </div>
                                        <div class="col-span-1">
                                            <p class="text-[12px] p-[16px] font-[500] text-[#95aac9]">PRICE</p>
                                        </div>
                                        <div class="col-span-1">
                                            <p class="text-[12px] p-[16px] font-[500] text-[#95aac9]">DATE</p>
                                        </div>
                                    </div>
                                    <div class="px-[8px] border-b-[1px] border-[#edf2f9]">
                                        <div class="flex flex-col justify-center items-center p-[16px]">
                                            <p class="text-[16px]">No Bid History</p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="md:col-span-1 p-2">
                        <div class="flex-col p-2">
                            <CountDown :countTime="countTime" />
                            <div class="flex-col justify-center items-center mt-[20px]">
                                <div class="text-[38px] font-[600] text-center">
                                    $954,342
                                </div>
                                <div class="text-[16px] text-center">
                                    Starting Bid
                                </div>
                            </div>
                            <div class="mt-[50px] flex justify-between">
                                <div class="border-b-[1px] border-black border-dashed">
                                    <p class="text-[17px] font-[600] leading-7">
                                        Bid Deposit
                                    </p>
                                </div>
                                <div class="flex items-center">
                                    <p class="text-[16px]">
                                        Required
                                    </p>
                                </div>
                            </div>
                            <div class="mt-[30px] flex justify-between">
                                <div class="border-b-[1px] border-black border-dashed">
                                    <p class="text-[17px] font-[600] leading-7">
                                        Cash Only
                                    </p>
                                </div>
                                <div class="flex items-center">
                                    <p class="text-[16px]">
                                        No
                                    </p>
                                </div>
                            </div>
                            <div class="mt-[50px] mb-[5px] flex">
                                <p class="text-[14px] text-[#344054b3] ">
                                    Note: The seller may choose to negotiate with bidders even if the reserve price
                                    isn't met.
                                </p>
                            </div>
                            <div class="mt-[40px] w-full">
                                <div class="flex flex-wrap justify-start items-stretch">
                                    <label for="search"
                                        class="mb-2 text-sm font-medium text-gray-900 sr-only dark:text-white">Search</label>
                                    <div class="relative w-full">
                                        <div
                                            class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none text-[21px] text-[#000000ad] ">
                                            $
                                        </div>
                                        <input type="number" id="search"
                                            class="block w-full p-4 pl-10 text-sm text-gray-900 border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:outline-none"
                                            placeholder="Search" required>
                                        <button type="submit"
                                            class="text-white absolute top-0 right-0 bottom-0 bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-tr-lg rounded-br-lg text-sm px-4 py-2 ">Place
                                            Bid</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <Footer />
    </div>
</template>
<script>
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
import Carousel from '@/components/Carousel.vue'
import CountDown from '@/components/CountDown.vue'

export default {
    components: {
        Header,
        Footer,
        Carousel,
        CountDown
    },
    data() {
        return {
            urls: ['https://i.insider.com/5c0fe5ba77a16512fd3d206e?width=700', 'https://i.insider.com/5c0fe5ba77a16512fd3d206e?width=700', 'https://i.insider.com/5c0fe5ba77a16512fd3d206e?width=700', 'https://i.insider.com/5c0fe5ba77a16512fd3d206e?width=700'],
            countTime: 197533,
        }
    },
}
</script>
