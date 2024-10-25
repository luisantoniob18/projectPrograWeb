<template>
  <div class="products-list">
    <!-- Recorremos la lista de productos y mostramos el componente ProductSimple para cada uno -->
    <nuxt-link
      v-for="(product, index) in products"
      :key="index"
      :to="`/product/${product.id}`" 
      @click.prevent="selectProduct(product)"
    >
      <ProductSimple :product="product" />
    </nuxt-link>

    <ProductDetailFullContent v-if="selectedProduct" :product="selectedProduct"/>
  </div>
</template>

<script>
import ProductSimple from '@/components/elements/product/ProductSimple';
//import product from '~/store/product';
import ProductDetailFullContent from '~/components/elements/detail/ProductDetailFullContent.vue';
import RelatedPosts from '~/components/partials/post/RelatedPosts.vue'; // Asegúrate de importar tus componentes
import PostComments from '~/components/partials/post/PostComments.vue'; // Asegúrate de importar tus componentes

export default {
  components: {
    ProductSimple,
    ProductDetailFullContent,
  },
  data() {
    return {
      products: [
        {
          id: 1,
          name: "Smart TV Samsung 50\"",
          vendor: "Samsung",
          ratingCount: 45,
          price: 799,
          thumbnail: {
            url: "default-thumbnail.jpg",
          },
        },
        {
          id: 2,
          name: "Smart TV LG 55\"",
          vendor: "LG",
          ratingCount: 50,
          price: 899,
          thumbnail: {
            url: "default-thumbnail.jpg",
          },
        },
        {
          id: 3,
          name: "Smart TV Sony 65\"",
          vendor: "Sony",
          ratingCount: 30,
          price: 1099,
          thumbnail: {
            url: "default-thumbnail.jpg",
          },
        },
        {
          id: 4,
          name: "Smart TV TCL 75\"",
          vendor: "TCL",
          ratingCount: 20,
          price: 1299,
          thumbnail: {
            url: "default-thumbnail.jpg",
          },
        },
        // Agrega más productos aquí si es necesario
      ],
      selectedProduct: null,
    };
  },

  methods: {
    selectProduct(product) {
      console.log(product);
      this.selectedProduct = product;
    }
  },

};



</script>

<style scoped>
.products-list {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

router-link {
  text-decoration: none; /* Quitar el subrayado del enlace */
}
</style>
