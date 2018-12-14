<template>
    <div>
        <p>
            滚动条最大高度:{{max}} 滚动条当前位置:{{scrollTop}}
        </p>
        <div ref="hello" class="hello">
            <p v-for="i in 1000" :key="i">{{i}}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'HelloWorld',
        data() {
            return {
                max: 0,
                scrollTop: 0,
            }
        },
        props: {
            msg: String
        },
        methods: {
            scroll() {
                const top = this.$refs.hello.scrollTop
                this.$set(this.$data, 'scrollTop', top)
            }
        },
        mounted() {
            const max = this.$refs.hello.scrollHeight
            this.$set(this.$data, 'max', max);
            this.$refs.hello.addEventListener('scroll', this.scroll)
        }
    }
</script>

<style scoped>
    .hello {
        height: 500px;
        width: 100px;
        background-color: antiquewhite;
        overflow: scroll;
        margin: auto;
    }
</style>
