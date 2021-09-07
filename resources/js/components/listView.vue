<template>
    <div>
        <div v-for="(item, index) in items" :key="index">
            <list-item
            :item="item"
            v-on:reloadToDos="getToDos()"
            class="item"
            />
        </div>
    </div>

</template>

<script>
import listItem from './listItem.vue'
export default {

    components:{
        listItem
    },

    data: function() {
        return {
            items:[]
        }
    },

    methods: {
        getToDos(){
            axios.get('api/todos').then(response=>{
                if(response.status == 200){
                    this.items = response.data.todos
                }
            })
        }
    },

    created() {
        this.getToDos();
    },
}
</script>

<style scoped>

</style>
