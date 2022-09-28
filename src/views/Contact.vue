<template>
  <div class="pa-0">
  <v-list
      subheader
      two-line
      flat
    >
      <v-text-field
            filled
            label="Add contact"
            append-icon="mdi-account-plus"
            hide-details
            clearable
            v-model="newContact"
            @click:append="addContact"
            @keyup.enter="addContact"
           >
         </v-text-field>
         
       
        <v-list-item v-for="contact in contacts" :key="contact.id">
          <template v-slot:default="{ active, }">
            <v-list-item-action>
              
              <v-checkbox
                :input-value="active"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>{{contact.name}} </v-list-item-title>
              <v-list-item-title>{{contact.number}}</v-list-item-title>
              
              <v-divider></v-divider>
            </v-list-item-content>
             <v-list-item-action>
          <v-btn icon
          @click="deleteContact(contact.id)">
            <v-icon color="red">mdi-delete</v-icon>
          </v-btn>
        </v-list-item-action>
          </template>
          
        </v-list-item>
        

     

    </v-list>
  </div>
</template>
<script>

  export default {
    data(){
      return{
        newContact:"",
        contacts:[
        //   {
        //   id: "",
        //   name:""
        // },
        // {
        //   id: 2,
        //   name:"Philani",
        //   number: "0767677219"
        // },
        // {
        //   id: 3,
        //   name:"Sindile",
        //   number: "0612998402"

        // }
      ]
      }
    },
    methods:{
      deleteContact(id){
        this.contacts = this.contacts.filter(contact =>
        contact.id !== id)
      },
      addContact(){
        let newContact = {
          id: Date.now(),
          name: this.newContact
        }
        this.contacts.push(newContact),
        localStorage.name = this.name;
        console.log('now pretend I did more stuff...')
      },
     
    },
    mounted() {
    if(localStorage.name) this.name = localStorage.name;
  },
  watch:{
    name(newName) {
      localStorage.name = newName;
    }
  }
  }
</script>
