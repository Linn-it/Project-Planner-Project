<template>
    <h3 class="text-center">Add Product</h3>
    <div class="add-product-form d-none d-md-block">
        <form @submit.prevent="addProduct">
            <div class="form-floating mb-3">
            <input v-model="title" type="text" class="form-control" id="floatingInput" placeholder="name@example.com" required>
            <label for="floatingInput">Product Title</label>
        </div>
        <div class="form-floating">
            <input v-model="detail" type="text" class="form-control" id="floatingInput" placeholder="productDetail" required>
            <label for="floatingInput">Product Detail</label>
        </div>
        <div class="text-center mt-4">
            <button class="btn btn-primary">Add Product</button>
        </div>
        </form>
    </div>

    <div class="add-product-form-phone d-block d-md-none">
        <form @submit.prevent="addProduct">
            <div class="form-floating mb-3">
            <input v-model="title" type="text" class="form-control" id="floatingInput" placeholder="name@example.com" required>
            <label for="floatingInput">Product Title</label>
        </div>
        <div class="form-floating">
            <input v-model="detail" type="text" class="form-control" id="floatingInput" placeholder="productDetail" required>
            <label for="floatingInput">Product Detail</label>
        </div>
        <div class="text-center mt-4">
            <button class="btn btn-primary">Add Product</button>
        </div>
        </form>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                title: '',
                detail: '',
            }
        },
        methods: {
            addProduct() {
                fetch('http://localhost:3000/Product',{
                    method : "POST",
                    headers : {
                        'Content-Type' : 'application/json'
                    },
                    body : JSON.stringify({
                        title : this.title,
                        detail : this.detail,
                        isShow : false
                    })
                })
                .then(_=> this.$router.push('/'))
            }
        },
    }
</script>

<style scoped>
.add-product-form{
    width: 450px;
    margin: 40px auto;
}

.add-product-form-phone{
    width: 300px;
    margin: 40px auto;
}
</style>