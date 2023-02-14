<template>
    <div class="z-0 flex flex-col items-center">
        <div class="pr-2">
            <div class="flex flex-col items-center relative">
                <div class="w-full">
                    <div @click="isShow = !isShow" class="my-6 p-1 flex border min-w-[180px] border-gray-200 bg-white rounded">
                        <div class="flex flex-auto flex-wrap">
                            <div v-for="selectedItem in selectedOptions"
                                class="flex justify-center items-center m-1 font-medium py-1 px-2 rounded-full text-teal-700 bg-teal-100 border border-teal-300 ">
                                <div class="text-xs font-normal leading-none flex-initial">{{ selectedItem }}
                                </div>
                                <div class="flex flex-auto flex-row-reverse" @click="removeSelectedOption(selectedItem)">
                                    <div>
                                        <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="none"
                                            viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"
                                            stroke-linecap="round" stroke-linejoin="round"
                                            class="feather feather-x cursor-pointer hover:text-teal-400 rounded-full w-4 h-4 ml-2">
                                            <line x1="18" y1="6" x2="6" y2="18"></line>
                                            <line x1="6" y1="6" x2="18" y2="18"></line>
                                        </svg>
                                    </div>
                                </div>
                            </div>
                            <div class="flex-1">
                                <input v-if="!selectedOptions.length" :placeholder="placeholder"
                                    class="bg-transparent p-1 px-2 appearance-none outline-none h-full w-full text-gray-800">
                                </div>
                        </div>
                        <div
                            class="text-gray-300 w-8 py-1 pl-2 pr-1 border-l flex items-center border-gray-200">
                            <button class="cursor-pointer w-6 h-6 text-gray-600 outline-none focus:outline-none">
                                <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="none"
                                    viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                                    stroke-linejoin="round" class="feather feather-chevron-down w-4 h-4">
                                    <polyline points="18 15 12 9 6 15"></polyline>
                                </svg>
                            </button>
                        </div>
                    </div>
                </div>
                <div
                    v-if="isShow"
                    class="absolute shadow top-[80%] z-5 bg-white w-full lef-0 rounded max-h-[300px] overflow-y-auto">
                    <div class="flex flex-col w-full">
                        <div v-for="item in unselectedOptions" @click="addSelectedOption(item)"
                            class="cursor-pointer w-full border-gray-100 rounded-t border-b hover:bg-teal-100">
                            <div
                                class="flex w-full items-center p-2 pl-2 border-transparent border-l-2 relative hover:border-teal-100">
                                <div class="w-full items-center flex">
                                    <div class="mx-2 leading-6">{{ item }}</div>
                                </div>
                            </div>
                        </div>
                        <div v-if="!unselectedOptions.length"
                            class="cursor-pointer w-full border-gray-100 rounded-t border-b hover:bg-teal-100">
                            <div
                                class="flex w-full items-center p-2 pl-2 border-transparent border-l-2 relative hover:border-teal-100">
                                <div class="w-full items-center flex">
                                    <div class="mx-2 leading-6">No results found</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import _ from "lodash";
export default {
    props: {
        optionData: Array,
        placeholder: String
    },
    data() {
        return {
            isShow: false,
            selectedOptions: [],
            unselectedOptions: []
        }
    },
    mounted() {
        console.log('props', this.optionData)
        this.unselectedOptions = _.cloneDeep(this.optionData)
    },
    methods: {
        addSelectedOption(option) {
            this.selectedOptions.push(option);
            this.unselectedOptions = this.unselectedOptions.filter((item) => item !== option)
        },
        removeSelectedOption(option) {
            this.unselectedOptions.push(option);
            this.selectedOptions = this.selectedOptions.filter((item) => item !== option)
        }
    }
}

</script>