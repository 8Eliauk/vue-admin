<template>
    <div>
        <div class="card-header">
            <span>{{title}}</span>
            <svg t="1652974455753" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2970" width="26" height="26"><path d="M512 179.2a332.8 332.8 0 1 1 0 665.6 332.8 332.8 0 0 1 0-665.6z m0 51.2a281.6 281.6 0 1 0 0 563.2 281.6 281.6 0 0 0 0-563.2z" p-id="2971" fill="#707070"></path><path d="M512.768 339.968a38.7072 38.7072 0 1 1 0 77.3632 38.7072 38.7072 0 0 1 0-77.3632zM546.4576 678.6048h-27.2384c-14.2848 0-29.0304-12.3904-29.0304-23.7056V498.0224h-9.728a25.8048 25.8048 0 1 1 0-51.6096s31.488-0.1024 32.3072 0c13.1072 0.9728 22.5792 6.656 22.5792 17.3568v163.2768h11.1104a25.8048 25.8048 0 1 1 0 51.5584z" p-id="2972" fill="#707070"></path></svg>
        </div>
        <div class="card-content">{{count}}</div>
        <div class="card-charts">
            <slot name="charts"></slot>
        </div>
        <div class="card-footer">
            <slot name="footer"></slot>
        </div>
    </div>
</template>

<script>
    export default {
        name:'Detail',
        props:['title','count']
    }
</script>

<style scoped>
.card-header {
    display: flex;
    justify-content: space-between;
    color: #d9d9d9;
}
.card-content {
    font-size: 30px;
    padding: 10px 0px;
}
.card-charts {
    height: 50px;
}
.card-footer {
    border-top: 1px solid #eee;
    padding-top: 10px;
}
</style>