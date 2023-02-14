<template>
    <div class="w-[280px] m-auto">
        <div class="flex flex-col border rounded-lg overflow-hidden">
            <div class="w-full h-[150px]">
                <img class="w-full h-full" src="https://www.auctions.re/public/images/b6698e6b-0637-4261-af41-048c57659d69-Trace_Construction_Outdoor_Living_Photo_by_Reed_Brown.webp?_wwcv=48">
            </div>
            <div class="my-2 flex-col justify-between item-start px-6">
                <div>
                    <p class="text-[12px] text-[#71717a]">
                        Listed by {{ auctionData.name }}
                    </p>
                </div>
                <div>
                    <h3 class="text-[14px] font-bold">
                        {{ auctionData.address }}
                    </h3>
                </div>
                <div>
                    <h3 class="text-[14px] font-bold">
                        {{ auctionData.state }}
                    </h3>
                </div>
            </div> 
            <div class="mb-[11px] flex px-6">
                <div class="flex">
                    <div class="flex flex-wrap justify-center items-stretch">
                        <div class="w-[18px] flex mr-[4px] ">
                            <img class="w-full h-full" src="https://www.auctions.re/public/images/bed-02.svg?_wwcv=48" />
                        </div>
                        <div class="mr-[10px]">
                            <p class="text-[12px]">{{ auctionData.bed }} Beds</p>
                        </div>
                    </div>
                    <div class="flex flex-wrap justify-center items-stretch">
                        <div class="w-[18px] flex mr-[4px] ">
                            <img class="w-full h-full" src="https://www.auctions.re/public/images/sink.svg?_wwcv=48" />
                        </div>
                        <div class="mr-[10px]">
                            <p class="text-[12px]">{{ auctionData.bath }} Baths</p>
                        </div>
                    </div>
                    <div class="flex flex-wrap justify-center items-stretch">
                        <div class="w-[18px] flex mr-[4px] ">
                            <img class="w-full h-full" src="https://www.auctions.re/public/images/lot.svg?_wwcv=48" />
                        </div>
                        <div class="mr-[10px]">
                            <p class="text-[12px]">{{ auctionData.ft }} ft</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="border-t-[1px] border-t-[#e4e4e7] ">
                <div class="flex flex-wrap justify-between items-stretch px-[14px] py-[3px]">
                    <div class="flex-col justify-start items-stretch p-[8px]">
                        <div class="mb-[4px]">
                            <p class="text-[10px]"></p>
                        </div>
                        <div class="text-[18px] font-bold">
                            ${{ auctionData.cost }}
                        </div>
                    </div>
                    <div class="flex-col justify-start items-stretch p-[8px]">
                        <button type="button"
                        class="w-full px-[15px] rounded-[8px] py-[8px] text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium text-sm text-center mr-3 md:mr-0">View Details</button>
                    </div>
                </div>
            </div>  
        </div>
    </div>
</template>

<script>
export default {
    props: {
        auctionData: Object
    }
}
</script>