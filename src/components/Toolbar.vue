<template>
  <div>
    
    <v-toolbar> 
      <v-toolbar-title>Timesheet</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-dialog v-model="dialog" max-width="800px">
      <template v-slot:activator="{ on }">
          <v-btn color="primary" dark class="mb-2" v-on="on">New Task</v-btn>
      </template>
      </v-dialog>
    </v-toolbar>
    <template>

  <v-data-table
    :headers="headers"
    :items="desserts"
    :search="search"
    sort-by="calories"
    class="elevation-1"
  >

    <template v-slot:top>
      <v-toolbar flat color="white">
        <v-toolbar-title>dfds</v-toolbar-title>
        <v-divider
          class="mx-4"
          inset
          vertical
        ></v-divider>
        <v-spacer></v-spacer>
        <v-dialog v-model="dialog" max-width="800px">
          <template v-slot:activator="{ on }">
          
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search"
              single-line
              hide-details
            ></v-text-field>
          
          </template>
          
          <v-card>
            <v-card-title>
              <span class="headline">{{ formTitle }}</span>
            </v-card-title>

            <v-card-text>
              <v-container >
                
                <v-row align="center">
                  <v-col cols="12" sm="6" md="6">
                    <v-text-field v-model="editedItem.name" label="Job Name"></v-text-field>
                  </v-col>
                  <v-col cols="12" sm="6" md="6">
                    <v-text-field v-model="editedItem.carbs" label="Deadline"></v-text-field>
                  </v-col>
                  <v-col cols="12" sm="6" md="6">
                    <v-textarea
                     outlined
                     name="input-7-4"
                     label="job Detail"
                     value=""
                    ></v-textarea>
                  </v-col>
       <v-col cols="12" sm="6" md="6">          
       <v-select
        v-model="TechnologySelect"
        :items="Technology"
        label="Base On Technology"
        style="max-width: 500px;"
        item-text=""
        item-value=""
        filled
        clearable
        chips
        multiple
        outlined
      ></v-select></v-col>
       <v-col cols="12" sm="6" md="6">
       <v-select
        v-model="jobGroupSelect"
        :items="jobGroup"
        label="jobGroup"
        style="max-width: 500px;"
        item-text="name"
        item-value="id"
        filled
        clearable
        chips
        outlined
       ></v-select></v-col>
                  
      <v-col cols="12" sm="6" md="6">
      <v-select
        v-model="BrandSelect"
        :items="Brand"
        label="Base On Brand"
        style="max-width: 500px;"
        item-text=""
        item-value=""
        filled
        clearable
        chips
        multiple
        outlined
      ></v-select></v-col>
       <v-col cols="12" sm="6" md="6">
      <v-select
        v-model="jobSowSelect"
        :items="newjobSow"
        label="jobSow"
        item-text="name"
        style="max-width: 500px;"
        item-value="id"
        filled
        clearable
        chips
        outlined
      ></v-select></v-col>
                  <v-col cols="12" sm="6" md="6">
                    <v-text-field v-model="editedItem.fat" label="Project-Track"></v-text-field>
                  </v-col>
      
                </v-row>
              </v-container>
            </v-card-text>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn x-large color="blue darken-1"  text @click="close">Cancel</v-btn>
              <v-btn x-large color="success darken-1" text @click="save">Save</v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-toolbar>
    </template>
    <template v-slot:item.action="{ item }">
      <v-icon
        small
        class="mr-2"
        @click="editItem(item)"
      >
        mdi-pencil-outline
      </v-icon>
      <v-icon
        small
        @click="deleteItem(item)"
      >
        mdi-delete
      </v-icon>
    </template>
    <template v-slot:no-data>
      <v-btn color="primary" @click="initialize">Reset</v-btn>
    </template>
  </v-data-table>
</template>
  </div>
</template>
<script>

// @ is an alias to /src

//import Toolbar from '@/components/Toolbar.vue'



  export default {
 //   name: 'toolbar',
 // components: {
  //Toolbar,
 // },

    data: () => ({
    dialog: false,
    search: '',
    headers: [
      {text: 'Id', value: 'auto'},
      {
        text: 'Name',
        align: 'left',
        sortable: false,
        value: 'name',
      },
      { text: 'Detail', value: 'calories' },
      { text: 'Hours', value: 'fat' },
      { text: 'Deadline', value: 'carbs' },
      { text: 'Brand', value: 'protein' },
      { text: 'Actions', value: 'action', sortable: false },
    ],
    
  ///////////////////////////////////////////////////////jobGroup
jobGroupSelect:'',
jobSowSelect:'',

     jobGroup: [
       {id: 1, name:'Documentation'},
       {id: 2, name:'POC with vServe Plus'},
       {id: 3, name:'Self POC by VST ECS'},
       {id: 4, name:'Trainer'},
       {id: 5, name:'Learning Skill'},
       {id: 6, name:'Event'},
       {id: 7, name:'Persent-Speaker'},
       {id: 8, name:'Solution'},
       {id: 9, name:'Sales Support'},
       {id: 10, name:'Services Support'},
       {id: 11, name:'Internal Operation Support'},
       {id: 12, name:'Business Traveling'},
       {id: 13, name:'Vender Support'}
     ],

     jobSow: [
       {name: 'Draft TOR [8]', jobGroupId: 1},
       {name: 'BoM [2]', jobGroupId: 1},
       {name: 'Manual and guide line [4]', jobGroupId: 1},
       {name: 'Technology comparison information [4]', jobGroupId: 1},
       {name: 'Comply [8]', jobGroupId: 1},
       {name: 'Propare presentation [4]', jobGroupId: 1},


       {name: 'Prove of Concept with vServe Plus [8]', jobGroupId: 2},
       {name: 'Implement, Installation and configuration [8]', jobGroupId: 2},
       {name: 'POC Professional Report [8]', jobGroupId: 2},


       {name: 'Prove of Concept [8]', jobGroupId: 3},
       {name: 'Prepare technical config [8]', jobGroupId: 3},
       {name: 'Technical Knowledge [8]', jobGroupId: 3},
       {name: 'Technical certify [8]', jobGroupId: 3},
       {name: 'Technical Testing [8]', jobGroupId: 3},
       {name: 'POC Professional Report [8]', jobGroupId: 3},

       {name: 'Trainer course [4]', jobGroupId: 4},
       {name: 'Trainee transfer [4]', jobGroupId: 4},
       {name: 'Vendor Assistant Trainee [4]', jobGroupId: 4},
       {name: 'Trainer course. [8]', jobGroupId: 4},
       {name: 'Trainee transfer. [8]', jobGroupId: 4},
       {name: 'Vendor Assistant Trainee. [8]', jobGroupId: 4},


       {name: 'Online Training [4]', jobGroupId: 5},
       {name: 'Certificated [4]', jobGroupId: 5},
       {name: 'Take Technical Course [4]', jobGroupId: 5},
       {name: 'Technical WorkShop [4]', jobGroupId: 5},
       {name: 'Self Training [4]', jobGroupId: 5},
       {name: 'Online Training. [8]', jobGroupId: 5},
       {name: 'Certificated. [8]', jobGroupId: 5},
       {name: 'Take Technical Course. [8]', jobGroupId: 5},
       {name: 'Technical WorkShop. [8]', jobGroupId: 5},
       {name: 'Self Training. [8]', jobGroupId: 5},


       {name: 'Attendance Vendor or Business event [4]', jobGroupId: 6},
       {name: 'Seminar [4]', jobGroupId: 6},
       {name: 'Technical Brief [4]', jobGroupId: 6},
       {name: 'Technology Updated Intend [4]', jobGroupId: 6},
       {name: 'Attendance Vendor or Business event. [8]', jobGroupId: 6},
       {name: 'Seminar. [8]', jobGroupId: 6},
       {name: 'Technical Brief. [8]', jobGroupId: 6},
       {name: 'Technology Updated Intend. [8]', jobGroupId: 6},


       {name: 'Support Presentation [4]', jobGroupId: 7},
       {name: 'Lead/Assissts Speaker [4]', jobGroupId: 7},
       {name: 'Lead partner trainee [4]', jobGroupId: 7},
       {name: 'Attendance Vendor or Business event [4]', jobGroupId: 7},
       {name: 'Technical Brief [4]', jobGroupId: 7},
       {name: 'Support Presentation. [8]', jobGroupId: 7},
       {name: 'Lead/Assissts Speaker. [8]', jobGroupId: 7},
       {name: 'Lead partner trainee. [8]', jobGroupId: 7},
       {name: 'Attendance Vendor or Business event. [8]', jobGroupId: 7},
       {name: 'Technical Brief. [8]', jobGroupId: 7},


       {name: 'Architect Design [8]', jobGroupId: 8},
       {name: 'Live Demo [4]', jobGroupId: 8},
       {name: 'Solution room [8]', jobGroupId: 8},
       {name: 'Implementation [8]', jobGroupId: 8},
       {name: 'Project Initiative [8]', jobGroupId: 8},
     ],

     ///////////////////////////////Technology/////////////////
     Technology:['Cloud','VM Infrastructure','Network','Security','Software','Image Process','Peripheral','Auto ID','Bigdata','IoT','appliance'],

     TechnologySelect:[],

     ////////////////////////////////Brand////////////////////////
     BrandSelect:[],

     Brand:['Acronis','ARISTA','Bluecoat','Cloud','Dell','DELLEMC','EasiSare','F5','Fireeye','Fortinet','Fujitsu','Honeywell','Huawei','Microsoft','NetApp','Nutanix','Quest','RedHat','Rubrik','SendQuick','Symantec','Veeam','Veritas','VMware','Webnic','Hortonworks','Oracle','Dell IoT Gateway','ThingWorx','Giga Central','Kaspersky','XYZ','Cumulocity','Arrow','Freewave','HIP','YITU','Gorilla','D-Link'],

    desserts: [],
    editedIndex: -1,
    editedItem: {
      name: '',
      calories: '',
      fat: '',
      carbs: '',
      protein: '',
    },
    defaultItem: {
      name: '',
      calories: '',
      fat: '',
      carbs: '',
      protein: '',
    },
  }),

  computed: {
    formTitle () {
      return this.editedIndex === -1 ? 'Add New Task' : 'Edit Task'
    },
    newjobSow(){
       return this.jobSow.filter(i => {
         return i.jobGroupId === this.jobGroupSelect
       })
     }
  },

  watch: {
    dialog (val) {
      val || this.close()
    },
  },

  created () {
    this.initialize()
  },

  methods: {
    initialize () {
      this.desserts = [
        {
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
        },
        {
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
        },
        {
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
        },
        {
          name: 'Gingerbread',
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
        },
        {
          name: 'Jelly bean',
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
        },
        {
          name: 'Lollipop',
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
        },
        {
          name: 'Honeycomb',
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
        },
        {
          name: 'Donut',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
        },
        {
          name: 'KitKat',
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
        },
      ]
    },

    editItem (item) {
      this.editedIndex = this.desserts.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem (item) {
      const index = this.desserts.indexOf(item)
      confirm('คุณต้องการลบข้อมูลใช่ หรือ ไม่?') && this.desserts.splice(index, 1)
    },

    close () {
      this.dialog = false
      setTimeout(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      }, 300)
    },

    save () {
      if (this.editedIndex > -1) {
        Object.assign(this.desserts[this.editedIndex], this.editedItem)
      } else {
        this.desserts.push(this.editedItem)
      }
      this.close()
    },
  },
}

</script>
