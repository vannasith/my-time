<template>
<nav>
     <v-app-bar
      app
      color="primary"
      dark
    >
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <div class="d-flex align-center">
      
        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="http://www.vstecs.co.th/en/images/vstecs-logo-02.png"
          width="100"
        />
      </div>

      <v-btn
        href="/"
        rounded color="primary" 
        dark
      >
        <span class="mr-2">Home</span>
        <v-icon></v-icon>
      </v-btn>

       <v-btn 
       href="/toolbar"
        rounded color="primary" 
        dark
      >
      
        <span class="mr-2">Calendar</span>
        <v-icon></v-icon>
      </v-btn>

       <v-btn 
        href="/about"
        rounded color="primary" 
        dark
      >
        <span class="mr-2">Timesheet</span>
        <v-icon></v-icon>
      </v-btn>

       <v-btn
        href="/test"
        rounded color="primary" 
        dark
      >
        <span class="mr-2">Project</span>
        <v-icon></v-icon>
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn
        href="#"
        rounded color="primary" 
        dark
      >
        <span class="mr-2">sing out</span>
        <v-icon>mdi-account-arrow-right-outline</v-icon>
      </v-btn>
    </v-app-bar>
<v-navigation-drawer app v-model="drawer" >
  <v-card
    class="mx-auto"
    max-width="400"
  >
    <v-list>
      <v-list-item-group v-model="model" mandatory color="indigo">
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
        >
          <v-list-item-icon>
            <v-icon v-text="item.icon"></v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title v-text="item.text"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-card>

  </v-navigation-drawer>
</nav>
</template>

<script>
export default {
  
  data(){ 
       return{
      drawer:false,
     items: [
        {
          icon: 'mdi-calendar-month-outline',
          text: 'Calendar',
        },
        {
          icon: 'mdi-file-table-box-multiple',
          text: 'Timesheet',
        },
        {
          icon: 'mdi-clipboard-text-outline',
          text: 'Project',
        },
      ],
      model: 1,
    }
  }   
      }

</script>