<template lang="html">
    <ul class="menu--dropdown">
        <li v-for="item in menuCategories" :key="item.categoria">
            <nuxt-link :to="localePath(item.url)">
                {{ item.categoria }}
            </nuxt-link>
        </li>
    </ul>
</template>

<script>
import axios from 'axios';

export default {
    name: 'MenuCategories',
    data() {
        return {
            menuCategories: []  
        };
    },
    mounted() {
        this.fetchMenuCategories();
    },
    methods: {
        async fetchMenuCategories() {
            // Mapeo de categorías a URLs
            const urlMapping = {
                'Televisores': '/televisores',
                'Telefono': '/electronica',
                
            };

            try {
                const response = await axios.get('http://127.0.0.1:8000/api/categoria'); 
                this.menuCategories = response.data.map(item => ({
                    categoria: item.Categoria, 
                    url: urlMapping[item.Categoria] || '/default'
                }));
            } catch (error) {
                console.error('Error al obtener las categorías del menú:', error);
            }
        }
    }
};
</script>

<style lang="scss" scoped>

</style>