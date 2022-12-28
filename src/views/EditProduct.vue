<template>
    <h3 class="text-center">Edit Product</h3>
    <div class="edit-product-form d-none d-md-block">
        <form @submit.prevent="editProduct">
            <div class="form-floating mb-3">
            <input v-model="title" type="text" class="form-control" id="floatingInput" placeholder="name@example.com" required>
            <label for="floatingInput">Product Title</label>
        </div>
        <div class="form-floating">
            <input v-model="detail" type="text" class="form-control" id="floatingInput" placeholder="productDetail" required>
            <label for="floatingInput">Product Title</label>
        </div>
        <div class="text-center mt-4">
            <button class="btn btn-primary">Update Product</button>
        </div>
        </form>
    </div>

    <div class="edit-product-form-phone d-block d-md-none">
        <form @submit.prevent="editProduct">
            <div class="form-floating mb-3">
            <input v-model="title" type="text" class="form-control" id="floatingInput" placeholder="name@example.com" required>
            <label for="floatingInput">Product Title</label>
        </div>
        <div class="form-floating">
            <input v-model="detail" type="text" class="form-control" id="floatingInput" placeholder="productDetail" required>
            <label for="floatingInput">Product Title</label>
        </div>
        <div class="text-center mt-4">
            <button class="btn btn-primary">Update Product</button>
        </div>
        </form>
    </div>
</template>

<script>
    export default {
        props : ['id'],
        data() {
            return {
                title: '',
                detail: '',
            }
        },
        methods: {
            editProduct() {
                fetch('http://localhost:3000/Product/'+this.id,{
                    method : 'PATCH',
                    headers : {
                        'Content-Type' : 'application/json',
                    },
                    body : JSON.stringify({
                        title : this.title,
                        detail : this.detail,
                    })
                })
                .then(_=> this.$router.push('/'))
            }
        },
        mounted () {
            fetch('http://localhost:3000/Product/'+this.id)
            .then(response => response.json())
            .then(datas => {
                this.title = datas.title;
                this.detail = datas.detail;
            })
        },
    }
</script>

<style scoped>
.edit-product-form{
    width: 450px;
    margin: 40px auto;
}

.edit-product-form-phone{
    width: 300px;
    margin: 40px auto;
}
</style>