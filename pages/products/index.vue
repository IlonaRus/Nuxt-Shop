<template>
    <div>
        <div class="grid grid-cols-4 gap-5">
            <div v-for="product in products" :key="product">
                <ProductCard :product="product" />
            </div>
        </div>
    </div>
</template>

<script setup>
definePageMeta({
    layout: "products",
});

// Fetch products
const { data: products } = await useFetch("https://fakestoreapi.com/products");

useHead({
    title: "Nuxt Shop | Products",
    meta: [{ name: "description", content: "Nuxt 3 Products" }],
});
</script>
