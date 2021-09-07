<template>
    <div class="add-item">
        <input type="text" class="input form-control" placeholder="Add Item" v-model="item.name">
        <button class="btn btn-primary" @click="addItem()">Add Item</button>
    </div>
</template>

<script>
export default {
    data: function(){
        return{
            item:{
                name:""
            }
        }
    },

    methods: {
        addItem(){
            if(this.item.name !== ''){
                axios.post('api/todos/store', {
                    todo:this.item.name
                }).then(response =>{
                    if(response.status >= 200 && response.status < 300){
                        this.item.name = null;
                        this.$emit('reloadToDos');

                    }

                })
            }
        }
    },
}
</script>

<style scoped>

</style>
