<template>
    <div @dblclick="$emit('play-reminder', list.id )" 
    :class="[list.reminder ? 'reminder' : '', 'task']"  :key="list.id" v-for="list in list">
    <div >
<i class="fa-solid fa-basket-shopping"></i><h3>{{list.text}}</h3>
    <br />
    <br />
    <i class="fa-solid fa-store"></i><h3>{{list.store}}</h3>
    </div>
    
     <div class="trash"><i @click="onDelete(list.id)" class="fa-solid fa-trash-can"></i></div>
     </div>
</template>

<script>

export default {
    name: 'List',
    props: {
        list: Array
    },
    methods: {
        onDelete(id) {
            this.$emit('delete-list', id)
        }
    }
}
</script>

<style scoped>
.fas {
  color: red;
}
.task {
       display: flex;
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
    justify-content: space-between;
  
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3, i {
  display: inline;
  padding-left: 5px;
  justify-content: space-between;
}
.task, i{
    align-items: flex-end;
}
</style>

