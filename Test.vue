<template>
<div id="app">

            <fieldset>
                <legend>
                    Create New Person
                </legend>
                <div class="form-group">
                    <label>Name:</label>
                    <input  type="text"  v-model="newPerson.name"/>
                </div>
                <h1></h1>
                <div class="form-group">
                    <label>Age:</label>
                    <input type="text"  v-model="newPerson.age"/>
                </div>
                 <h1></h1>
                <div class="form-group">
                    <label>Sex:</label>
                    <select v-model="newPerson.sex">
                    <option value="Male">Male</option>
                    <option value="Female">Female</option>
                </select>
                </div>
                <h1></h1>
                <div class="form-group">
                    <label></label>
                    <button id="c-Button" @click="createPerson">Create</button>
                     <!-- <button id="c-Button" v-on:click="createPerson">Create</button> -->
                </div>
                <h1></h1>
        </fieldset>
        <!-- <table width=90% align=center border="1px" border-color=#42b983> -->
            <table  id="customers">
            <thead>
                <tr>
                    <th bgcolor=#42b983>Name</th>
                    <th bgcolor=#42b983>Age</th>
                    <th bgcolor=#42b983> Sex</th>
                    <th bgcolor=#42b983>Operation</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(person,index) in people"
                :key="person in people">
                <td>
                    <input type="text" v-model="person.name" v-if="editlist===index">
                    <span v-else>{{person.name}}</span>
                </td>
                 <td>
                    <input type="text" v-model="person.age" v-if="editlist===index">
                    <span v-else>{{person.age}}</span>
                 </td>
                <td>
                    <input type="text" v-model="person.sex" v-if="editlist===index">
                    <span v-else>{{person.sex}}</span>
                </td>
                    <td :class="'text-center'">
                        <button id="c-Button" @click="deletePerson(index)">Delete</button>
                        <button id="c-Button" @click="editPerson(index)">Edit</button>
                        <button id="c-Button" @click="save(index)">save</button>
                        <!-- <button id="c-Button" @click="submit">submit</button> -->
                        </td>
                    <!-- <td :class="'text-center'"><button id="c-Button" v-on:click="deletePerson($index)">Delete</button></td> -->
                </tr>
            </tbody>
        </table>
        </div>
   
</template>
<script>
export default {
    name:'HelloWorld',
    data(){
        return{
          editlist:'',
           newPerson: {
                    name: '',
                    age: 0,
                    sex: 'Male'
                },
                people: [{
                    name: 'Jack',
                    age: 30,
                    sex: 'Male'
                }, {
                    name: 'Bill',
                    age: 26,
                    sex: 'Male'
                }, {
                    name: 'Tracy',
                    age: 22,
                    sex: 'Female'
                }, {
                    name: 'Chris',
                    age: 36,
                    sex: 'Male'
                }],
        }
        },
            methods:{
                createPerson: function(){
                    this.people.push(this.newPerson);
                    // 添加完newPerson对象后，重置newPerson对象
                    this.newPerson = {name: '', age: 0, sex: 'Male'}
                },
                deletePerson: function(index){
                    // 删一个数组元素
                    this.people.splice(index,1);
                },
                editPerson:function(index){
                    this.editlist=index;
                },
                save:function(index){
                    this.editlist=!index;
                },
    //             submit:function () {
    //                 this.editist='';
    //                  console.log(JSON.stringify(this.people))
    //   }
                
            }
    }

</script>
<style>
#customers
{
	font-family:"Trebuchet MS", Arial, Helvetica, sans-serif;
	width:100%;
	border-collapse:collapse;
}
#customers td, #customers th 
{
	font-size:1em;
	border:1px solid #42b983;
	padding:3px 7px 2px 7px;
}
#customers th 
{
	font-size:1.1em;
	text-align:center;
	padding-top:5px;
	padding-bottom:4px;
	background-color:#42b983;
	color:#ffffff;
}
#customers tr.alt td 
{
	color:#000000;
	background-color:#EAF2D3;
}
</style>
<style>
#c-Button{
    background-color:#42b983;
    border-color:#42b983;
    border-radius: 4px;
}
</style>
<style>

</style>


