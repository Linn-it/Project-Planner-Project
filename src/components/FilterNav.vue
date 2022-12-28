<template>
    <div class="filter-nav-box d-none d-md-block">
        <button :class="{'active' : current === 'all'}" @click="filterBy('all')">All</button>
        <button :class="{'active' : current === 'complete'}" @click="filterBy('complete')">Complete</button>
        <button :class="{'active' : current === 'ongoing'}" @click="filterBy('ongoing')">Ongoing</button>
    </div>

    <div class="filter-nav-box-phone d-block d-md-none">
        <button :class="{'active' : current === 'all'}" @click="filterBy('all')">All</button>
        <button :class="{'active' : current === 'complete'}" @click="filterBy('complete')">Complete</button>
        <button :class="{'active' : current === 'ongoing'}" @click="filterBy('ongoing')">Ongoing</button>
    </div>
</template>

<script>
    export default {
        props : ['current'],
        methods: {
            filterBy(value) {
                this.$emit('filterVal',value)
            }
        },
    }
</script>

<style scoped>
.filter-nav-box{
    margin-left: 360px;
}

.filter-nav-box-phone{
    margin-left: 40px;
}

button{
    background-color: transparent;
    border: none;
    margin-right: 10px;
    text-transform: uppercase;
    letter-spacing: 2px;
    font-size: 14px;
    color: #333;
}

.active{
    color: #161616;
    font-weight: bold;
}
</style>