<template>
    <div class="product-box mx-auto d-none d-md-block" :class="{'success' : product.isDone}">
        <div class="d-flex justify-content-between align-items-center">
            <h3 class="mb-0" @click="showDetail = !showDetail">{{ product.title }}</h3>
            <div>
                <span @click="deleteProduct"><i class="bi bi-trash3 text-danger fw-bold"></i></span>
                <router-link :to="{name : 'EditProduct',params : {id : this.product.id}}">
                    <span><i class="bi bi-pencil-fill"></i></span>
                </router-link>
                <span @click="checkProduct"><i class="bi bi-check-lg text-info fw-bold fs-4"></i></span>
            </div>
        </div>
        <p class="mb-0 mt-3" v-if="showDetail">{{ product.detail }}</p>
    </div>

    <div class="product-box-phone mx-auto d-block d-md-none" :class="{'success' : product.isDone}">
        <div class="d-flex justify-content-between align-items-center">
            <h3 class="mb-0" @click="showDetail = !showDetail">{{ product.title }}</h3>
            <div>
                <span @click="deleteProduct"><i class="bi bi-trash3 text-danger fw-bold"></i></span>
                <router-link :to="{name : 'EditProduct',params : {id : this.product.id}}">
                    <span><i class="bi bi-pencil-fill"></i></span>
                </router-link>
                <span @click="checkProduct"><i class="bi bi-check-lg text-info fw-bold fs-4"></i></span>
            </div>
        </div>
        <p class="mb-0 mt-3" v-if="showDetail">{{ product.detail }}</p>
    </div>
</template>

<script>
    export default {
        props : ['product'],
        data() {
            return {
                showDetail: false,
                api : 'http://localhost:3000/Product/',
            }
        },
        methods: {
            deleteProduct() {
                fetch(this.api+this.product.id,{method : 'DELETE'})
                .then(_=> this.$emit('deleteProduct',this.product.id))
            },
            checkProduct(){
                fetch(this.api+this.product.id,{
                    method : 'PATCH',
                    headers : {
                        'Content-Type' : 'application/json'
                    },
                    body : JSON.stringify({
                        isDone : !this.product.isDone
                    })
                })
                .then(_=> this.$emit('checkProduct',this.product.id))
            }
        },
    }
</script>

<style scoped>
.product-box{
    width: 600px;
    background-color: #f2f2f2;
    padding: 25px;
    margin-bottom: 20px;
    border-radius: 15px;
    border-left: 10px solid crimson;
}

.product-box-phone{
    width: 350px;
    background-color: #f2f2f2;
    padding: 18px;
    margin-bottom: 20px;
    border-radius: 15px;
    border-left: 10px solid crimson;
}

h3{
    cursor: pointer;
    color: indigo;
}

span{
    cursor: pointer;
    margin-right: 10px;
    font-size: 19px;
}

.product-box-phone span{
    cursor: pointer;
    margin-right: 6px;
    font-size: 17px;
}

.success{
    border-left-color: green;
}

a{
    color: black;
}
</style>