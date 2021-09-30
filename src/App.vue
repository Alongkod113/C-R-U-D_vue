<template>
  <div id="app">
  <img alt="Vue logo" src="./assets/kids-160168_640.png" class="StudentPicture">
<div class="w3-container w3-blue">
  <h2>Input Form</h2>
</div>
<form class="w3-container">
  <p>
  <label>First Name</label>
  <input class="w3-input" type="text" v-model="form.Fname"></p>
  <p>
  <label>Last Name</label>
  <input class="w3-input" type="text" v-model="form.Lname"></p>
  <p>
  <label>Email</label>
  <input class="w3-input" type="text" v-model="form.age"></p>
</form>  
    <div style="padding-top: 20px;">
      <button
        v-if="isEdit"
        @click="update()" >
        update
      </button>
      <button 
        v-else
        @click="add()">
        submit
      </button>
    </div>
    <div style="padding-top: 40px;">
      <table class="table" border="1">
        <tr>
          <th> Fname </th>
          <th> Lname </th>
          <th> Age </th>
          <th></th>
          <th></th>
        </tr>
        <tr v-for="(item, i) in items" :key="i">
          <td>
            {{ item.Fname }} 
          </td>
          <td>
            {{ item.Lname }}
          </td>
          <td>
            {{ item.age }}
          </td>
          <td>
            <button @click="setUpdate(item, i)">
              Edit
            </button>
          </td>
          <td>
            <button @click="remove(i)">
              Delete
            </button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      form: {
        Fname: '',
        Lname: ' ',
        age: 0
      },
      items: [
        {
          Fname: 'Mark',
          Lname:'yuer',
          age: 18
        },
        {
          Fname: 'John',
          Lname:'yuer',
          age: 20
        },
        {
          Fname: 'David',
          Lname:'yuer',
          age: 25
        }
      ],
      isEdit: false, 
      updateIndex: null
    }
  },
  methods: {
    setDefault () {
      this.form = {
        Fname: '',
        Lname: ' ',
        age: 0
      }
    },
    add () {
      this.items.push(this.form) //this เราจะใช่ตัวเเปลในนี้
      this.setDefault()
    },
    remove (index) {
      this.items.splice(index, 1)
    },
    setUpdate (item, index) {
      this.form.Fname = item.Fname
      this.form.Lname = item.Lname
      this.form.age = item.age
      this.isEdit = true
      this.updateIndex = index
    },
    update () {
      this.items[this.updateIndex] = this.form //[] ทำงานเกี่ยวกับ index ไหน
      this.setDefault()
      this.isEdit = false
    }
  }
}
</script>

<style scoped>

  .table {
    font-family: Arial, Helvetica, sans-serif;
    border-collapse: collapse;
    width: 100%;
  }

  .table td, .table th {
    border: 1px solid #ddd;
    padding: 8px;
  }

  .table tr:nth-child(even){background-color: #f2f2f2;}

  .table tr:hover {background-color: #ddd;}

  .table th {
    padding-top: 12px;
    padding-bottom: 12px;
    text-align: left;
    background-color: #04AA6D;
    color: white;
  }
.StudentPicture{
  height: 200px;
  margin-top: 20px;
  margin-left: 555px;
}


</style>
