<template>
  
  <v-list
      subheader
      two-line
      flat
      class="pt-0"
    >
    <div>
      <v-text-field
            filled
            label="Add contact"
            append-icon="mdi-account-plus"
          hide-details
          clearabl 
          v-model="newContact"
          @click:append>
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
            <v-icon color="grey lighten-1">mdi-delete</v-icon>
          </v-btn>
        </v-list-item-action>
          </template>
          
        </v-list-item>
        

      </div>

    </v-list>
</template>
<script>

  export default {
    data(){
      return{
        newContact:"",
        contacts:[
          {
          id: 1,
          name:"Lunga",
          number: "0826738289"
        },
        {
          id: 2,
          name:"Philani",
          number: "0767677219"
        },
        {
          id: 3,
          name:"Sindile",
          number: "0612998402"

        }
      ]
      }
    },
    methods:{
      deleteContact(id){
        this.contacts= this.contacts.filter(contact =>
        contact.id !== id)
      },
      addContact(){
        let newContact ={
          id: Date.now(),
          title: this.newContactTitle
        }
      }
    }
  }
</script>
