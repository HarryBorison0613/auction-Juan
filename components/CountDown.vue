<template>
    <div>

    </div>
    <div class="flex justify-between">
        <div class="flex flex-col w-[40px]">
            <p class="text-[29px] font-bold text-center">{{ day }}</p>
            <P class="text-[14px] font-semibold text-center text-[#00000094]">DAYS</P>
        </div>
        <p class="text-[29px] font-bold">:</p>
        <div class="flex flex-col w-[40px]">
            <p class="text-[29px] font-bold text-center">{{ hour }}</p>
            <P class="text-[14px] font-semibold text-center text-[#00000094]">HOURS</P>
        </div>
        <p class="text-[29px] font-bold">:</p>
        <div class="flex flex-col w-[40px]">
            <p class="text-[29px] text-center font-bold">{{ minute }}</p>
            <P class="text-[14px] font-semibold text-center text-[#00000094]">MINS</P>
        </div>
        <p class="text-[29px] font-bold">:</p>
        <div class="flex flex-col w-[40px]">
            <p class="text-[29px] text-center font-bold">{{ second }}</p>
            <P class="text-[14px] font-semibold text-center text-[#00000094]">SECS</P>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        countTime: Number
    },
    data() {
        return {
            total: this.countTime,
            second: 0,
            minute: 0,
            hour: 0,
            day: 0,
            intervalId: ''
        }
    },
    mounted() {
        this.countDownTime()
    },
    beforeDestroy() {
        clearInterval(this.intervalId)
    },
    methods: {
        displayCountNumber(num) {
            if (Math.floor(num / 10) === 0) {
                return `0${num}`
            } else {
                return num
            }
        },
        countDownTime() {
            this.intervalId = setInterval(() => {
                this.total -= 1
                const secondValue = this.total % 60
                const minuteValue = Math.floor(this.total / 60) % 60
                const hourValue = Math.floor(this.total / 3600) % 24
                const dayValue = Math.floor(Math.floor(this.total / 3600) / 24)

                this.second = this.displayCountNumber(secondValue)
                this.minute = this.displayCountNumber(minuteValue)
                this.hour = this.displayCountNumber(hourValue)
                this.day = this.displayCountNumber(dayValue)
            }, 1000);
        }
    }
}
</script>