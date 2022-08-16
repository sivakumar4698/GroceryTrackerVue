<template>
    <div v-if="ShowAdd">
  <AddGrocery @add-list="addList"/>
  </div>
  <List :list= "list" @delete-list = "deleteList"
   @play-reminder ='playReminder' />
</template>

<script>
import List from '../components/List.vue'
import AddGrocery from '../components/AddGrocery.vue'

export default {
    name: 'Home',
    props:{
        ShowAdd: Boolean,
    },
    components: {
        List,
        AddGrocery
    },
    data() {
        return{
           list: [],
           

        }
    },
    methods: {
    async addList(newList){
      const res = await fetch('http://localhost:5000/list', {
        method: 'POST',
        headers: {
          'content-type': 'application/json',
        },
        body: JSON.stringify(newList)
      })

      const list = await res.json()

      this.list = [...this.list, list]
    },
    async deleteList(id) {
      const res = await fetch(`http://localhost:5000/list/${id}`, {
        method: 'DELETE'
      })

      res.status === 200 ? this.list = this.list.filter((item) => 
     item.id !== id) : alert('Error while performing the delete')
    },

    async playReminder(id) {

      const listToToggle = await this.getalist(id)
      const updateList = {
        ...listToToggle, reminder: !listToToggle.reminder
      }
      const res = await fetch(`http://localhost:5000/list/${id}`, {
        method: 'PUT',
        headers: {
          'content-type': 'application/json',
        },
        body: JSON.stringify(updateList)
      })

      const data = await res.json()

     this.list = this.list.map((item) =>
      item.id === id ? {
      ...item, reminder : data.reminder
      } : item)
      }, 

      async getlist() {
        const res = await fetch('http://localhost:5000/list')
         const list = await res.json()
         return list
      },

       async getalist(id) {
        const res = await fetch(`http://localhost:5000/list/${id}`)
         const alist = await res.json()
         return alist
      }
      
     
    },

  async created () {
    this.list = await this.getlist()
  }
}
</script>
