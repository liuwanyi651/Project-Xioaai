<template>
<div class="flex">
    <div class="left">
        欢迎来到{{user.username}}后台管理系统！
    </div>
    <div class="right">
        <div>{{user.username}}{{hi}}</div>
        <div>现在登录时间是：{{timer}}</div>
    </div>
</div>
</template>

<script>
import dayjs from 'dayjs'
export default {
    name: '',
    props: {},
    data() {
        return {
            user: {
                username: ''
            },
            hi: '',
            timer: '',
            time: '',
        }
    },
    components: {},
    methods: {
        getuser() {
            // localStorage.getItem 是获取存储的字符串
            // console.log(111);
            let userobj = localStorage.getItem("user");
            // console.log(localStorage.getItem("user"));
            // JSON.parse 把字符串转换成对象
            this.user = JSON.parse(userobj)
        },
        getTime() {
            this.timer = dayjs(new Date()).format(' YYYY/MM/DD/HH:mm:ss')
            setInterval(() => {
                if (dayjs().hour() >= 6 && dayjs().hour() <= 12) {
                    this.hi = "早上好！";
                } else if (dayjs().hour() >= 12 && dayjs().hour() <= 14) {
                    this.hi = "中午好！";
                } else if (dayjs().hour() >= 14 && dayjs().hour() <= 18) {
                    this.hi = "下午好！";
                } else if (dayjs().hour() >= 16 && dayjs().hour() <= 23) {
                    this.hi = "晚上好！";
                } else {
                    this.hi = "该睡觉啦！";
                }
            }, 1000)
            console.log(this.timer);
        }
    },
    mounted() {
        this.getuser()
        this.getTime()
    },
    computed: {},
    watch: {}
}
</script>

<style lang="scss" scoped>
.flex {
    display: flex;
    justify-content: space-between;
}

.left {
    width: 300px;
    // background: greenyellow;
}

.right {
    width: 500px;
    background: rgb(131, 110, 58);
    display: flex;
}
</style>
