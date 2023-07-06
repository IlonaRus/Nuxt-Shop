<template>
    <div class="card">
        <div class="grid grid-cols-2 gap-10">
            <div class="p-7">
                <img
                    :src="product.image"
                    alt="product image"
                    class="mx-auto my-7"
                />
            </div>
            <div class="p-7">
                <h2 class="text-4xl my-7">{{ product.title }}</h2>
                <p class="text-xl my-7">Prics - ${{ product.price }}</p>
                <h3 class="font-bold border-b-2 mb-4 pb-2">
                    Product description
                </h3>
                <p class="mb-7">{{ product.description }}</p>
                <button class="btn flex" @click="addToCart(product)">
                    <i class="material-icons mr-2">add_shopping_cart</i>
                    <span>Add to cart</span>
                </button>
            </div>
        </div>
    </div>
</template>

<script setup>
const { product } = defineProps(["product"]);

const addToCart = (product) =>
    fetch("https://fakestoreapi.com/carts", {
        method: "POST",
        body: JSON.stringify({
            userId: product.id,
            date: "2020-02-03",
            products: [{ productId: product.id, quantity: 1 }],
        }),
    })
        .then((res) => res.json())
        .then((json) => console.log(json));
</script>

<style scoped>
img {
    max-width: 400px;
}
</style>
