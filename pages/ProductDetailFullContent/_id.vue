<template>
    <div>
      <!-- Componente que muestra el detalle del producto -->
      <ProductDetailFullContent :productId="id" />
  
      <!-- Sección de publicaciones relacionadas -->
      <div class="container">
        <related-posts />
        <post-comments />
      </div>
    </div>
  </template>
  
  <script>
  import ProductDetailFullContent from '~/components/elements/detail/ProductDetailFullContent.vue';
  import RelatedPosts from '~/components/partials/post/RelatedPosts.vue'; // Asegúrate de importar tus componentes
  import PostComments from '~/components/partials/post/PostComments.vue'; // Asegúrate de importar tus componentes
  
  export default {
    components: {
      ProductDetailFullContent,
      RelatedPosts,
      PostComments
    },
    async asyncData({ params }) {
      return {
        id: params.id // Capturamos el parámetro 'id' desde la URL
      };
    }
  };
  </script>
  
  <style lang="scss" scoped>
  /* Aquí puedes agregar los estilos específicos si es necesario */
  </style>
  
