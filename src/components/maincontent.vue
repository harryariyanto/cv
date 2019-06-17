<template>
  <v-container pa-0 mt-4 elevation-5>
    <v-parallax dark :src="require('@/assets/images/parallax-images-1.jpg')" height="200">
      <v-layout align-center column justify-center>
        <h1 class="display-2 font-weight-thin mb-2">Harry's Portfolio</h1>
        <h4 class="subheading">Software Engineer</h4>
      </v-layout>
    </v-parallax>

    <v-layout text-xs-center wrap mx-0 mb-5 style="min-height:500px;">
      <v-flex xs2 amber darken-2>
        <v-list style="padding:0" three-line wrap class="amber darken-1">
          <template v-for="(item,index) in sectionHeader">
            <v-list-tile :key="index" avatar ripple @click="click=index">
              <v-list-tile-content>
                <v-list-tile-title class="headline">
                  <i class="material-icons">
                    {{item.icon}}
                  </i>
                  {{item.text}}
                </v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>
          </template>
        </v-list>
      </v-flex>
      <v-flex xs10>
        <v-layout align-center column fill-height>
          <div v-if="click==0" style="width:100%;">
            <div id="Header" class="px-2">
              <h1 class="headline font-weight-bold mt-3">
                About Me
              </h1>
              <div style="padding: 0px 45%">
                <v-divider style="background-color:gold;">
                </v-divider>
              </div>
              <div class="mt-4 font1 px-7 font-weight-regular font-italic">
                "A flexible software developer who is well-versed on web development technologies.
                Can work independently or in a team.
                Always aspiring to be a better person than before"
              </div>
            </div>
            <v-layout row mt-5 justify-center wrap>
              <v-flex md3 xs9 pa-2>
                <v-img :src="require('@/assets/images/photo.jpg')"
                  gradient="to top right, rgba(100,115,201,.1), rgba(42,42,43,.7)"></v-img>
              </v-flex>
              <v-flex xs12 md9 mb-3>
                <h3 class="headline font-weight-medium">Personal Info</h3>
                <div style="padding: 0px 45%">
                  <v-divider class="primary">
                  </v-divider>
                </div>

                <v-layout row mt-2>
                  <v-flex>
                    <h5 class="subheading ">Full Name</h5>
                    <h5 class="subheading ">Nationality</h5>
                    <h5 class="subheading ">Address</h5>
                    <h5 class="subheading ">Email</h5>
                    <h5 class="subheading ">Phone</h5>
                  </v-flex>
                  <v-flex>
                    <h5 class="subheading font-weight-bold">Harry Ariyanto Putra</h5>
                    <h5 class="subheading font-weight-bold">Indonesian</h5>
                    <h5 class="subheading font-weight-bold">Tongelresestraat, Eindhoven</h5>
                    <h5 class="subheading font-weight-bold">harryariyantop@gmail.com</h5>
                    <h5 class="subheading font-weight-bold">+31 621324706</h5>
                  </v-flex>
                </v-layout>
              </v-flex>
            </v-layout>
          </div>
          <div v-if="click==1" style="width:100%;">
            <div id="Header" class="px-2">
              <h1 class="headline font-weight-bold my-2">
                My Resume
              </h1>
              <div style="padding: 0px 40%">
                <v-divider style="background-color:gold;">
                </v-divider>
              </div>
              <div class="mt-5 mx-2">
                <h3 class="headline font-weight-medium font-italic text-lg-center">Experiences</h3>

                <v-timeline style="margin:1% 0%">
                  <v-timeline-item v-for="(item,index) in experiences" :key="index"
                    :color="`${item.color} lighten-2`" fill-dot>
                    <template v-slot:opposite>
                      <span :class="`headline font-weight-bold ${item.color}--text`"
                        v-text="item.date"></span>
                    </template>
                    <v-card>
                      <v-card-title :class="`${item.color} darken-2`">
                        <h3 class="display-1 white--text font-weight-light font1">{{item.title}}
                        </h3>
                        <br>
                      </v-card-title>
                      <v-layout align-start justify-space-between row mt-2>
                        <v-flex xs6>
                          <span class="body-2 font-weight-light">{{item.company}}</span>
                        </v-flex>
                        <v-flex xs6>
                          <span
                            class="caption font-weight-regular font-italic ">{{item.location}}</span>
                        </v-flex>
                      </v-layout>
                      <v-container px-1 pt-1>
                        <v-layout mt-1 mx-2 row>
                          <v-flex xs-8>
                            <h6 class="body-2 text-lg-left  font-weight-medium font-italic">Summary:
                            </h6>
                            <v-divider></v-divider>
                            <ul>
                              <li class="text-lg-justify caption font-weight-light"
                                v-for="(i,index) in item.description" :key=index>
                                {{i}}
                              </li>
                            </ul>
                          </v-flex>
                          <v-flex xs4 pl-3>
                            <v-layout justify-center align center column fill-height>
                              <v-menu open-on-hover :close-on-content-click="false"
                                :nudge-width="200" offset-x>
                                <template v-slot:activator="{ on }">
                                  <v-btn color="primary" flat dark v-on="on">
                                    <i class="material-icons">
                                      search
                                    </i>
                                  </v-btn>
                                </template>
                                <v-card>
                                  <div class="pa-2">
                                    <v-img pa-2 contain :src="item.imageLink"
                                      class="grey lighten-2" />
                                  </div>
                                </v-card>
                              </v-menu>

                            </v-layout>
                          </v-flex>
                        </v-layout>
                      </v-container>
                    </v-card>
                  </v-timeline-item>

                </v-timeline>
              </div>

              <div class="mt-5 mx-2">
                <h3 class="headline font-weight-medium font-italic text-lg-center">Education</h3>

                <v-timeline style="margin:1% 0%">
                  <v-timeline-item v-for="(item,index) in education" :key="index"
                    :color="`${item.color} lighten-2`" fill-dot small>
                    <template v-slot:opposite>
                      <span :class="`headline font-weight-bold ${item.color}--text`"
                        v-text="item.date"></span>
                    </template>
                    <v-card>
                      <v-card-title :class="`${item.color} darken-2`">
                        <h4 class="title white--text font-weight-light font1">{{item.title}}
                        </h4>
                        <br>
                      </v-card-title>
                      <v-layout align-start justify-space-between row mt-2>
                        <v-flex xs6>
                          <span class="body-2 font-weight-light">{{item.place}}</span>
                        </v-flex>
                        <v-flex xs6>
                          <span
                            class="caption font-weight-regular font-italic ">{{item.location}}</span>
                        </v-flex>
                      </v-layout>
                    </v-card>
                  </v-timeline-item>

                </v-timeline>

              </div>
              <div class="mt-5 mx-2">
                <h3 class="headline font-weight-medium font-italic text-lg-center">Skills
                </h3>
                <v-layout row mb-2>
                  <v-flex xs7>
                    <h5 class="text-lg-right mr-2 subheading font-italic font-weight-regular ">
                      Technical Skills
                    </h5>
                    <v-layout align-content-start justify-start reverse row wrap fill-height>
                      <v-chip :color="`${item.color} lighten-2 `" v-for="(item,index) in techskills"
                        :key=index>{{item.skill}}
                      </v-chip>
                    </v-layout>
                  </v-flex>
                  <v-flex xs1>
                    <v-layout align-center justify-center fill-height>
                      <i class="material-icons">
                        settings_ethernet
                      </i>
                    </v-layout>
                  </v-flex>
                  <v-flex xs7>
                    <v-layout column>
                      <v-flex>
                        <h5 class="text-lg-left ml-2 subheading font-italic font-weight-regular ">
                          Soft Skills</h5>
                        <v-layout align-content-start row wrap>
                          <v-chip :color="`${item.color} lighten-2 `"
                            v-for="(item,index) in softskills" :key=index>{{item.skill}}
                          </v-chip>
                        </v-layout>
                      </v-flex>
                      <v-flex>
                        <h5 class="text-lg-left ml-2 subheading font-italic font-weight-regular ">
                          Personal Traits
                        </h5>
                        <v-layout align-content-start row wrap>
                          <v-chip :color="`${item.color} lighten-2 `" v-for="(item,index) in traits"
                            :key=index>{{item.skill}}
                          </v-chip>
                        </v-layout>
                      </v-flex>
                    </v-layout>
                  </v-flex>
                </v-layout>

              </div>
            </div>
          </div>
          <div v-if="click==2" style="width:100%;">
            <div id="Header" class="px-2">
              <h1 class="headline font-weight-bold my-2">
                My Portfolio
              </h1>
              <div style="padding: 0px 40%">
                <v-divider style="background-color:gold;">
                </v-divider>
              </div>
              <div class="mt-5 mx-2">
                <v-container grid-list-xs fluid px-1>
                  <v-layout column>
                    <v-flex v-for="(item,index) in portfolio" :key="index">
                      <v-layout row>
                        <v-flex xs2>
                          <v-layout align-center justify-center fill-height>
                            <div class="subheading font-weight-medium font-italic">
                              {{item.name}}
                            </div>
                          </v-layout>
                        </v-flex>
                        <v-flex xs10>
                          <v-layout row wrap>
                            <v-flex v-if="item.img.length==0">
                              <h3 class="title font-weight-medium font-italic text-lg-center">Non
                                Disclosure Agreement</h3>
                            </v-flex>
                            <v-flex v-for="(image,n) in item.img" :key=n pa-2 v-else>
                              <v-menu open-on-hover :close-on-content-click="false"
                                :nudge-width="200" offset-x>
                                <template v-slot:activator="{ on }">
                                  <v-card tile flat v-on="on">
                                    <v-img :src="image"></v-img>
                                  </v-card>
                                </template>
                                <v-card>
                                  <div class="pa-2">
                                    <v-img pa-1 contain min-height="250px" min-width="500px" :src="image"
                                      class="grey lighten-2" />
                                  </div>
                                </v-card>
                              </v-menu>

                            </v-flex>
                          </v-layout>
                        </v-flex>
                      </v-layout>
                    </v-flex>
                  </v-layout>
                </v-container>
              </div>
            </div>
          </div>
        </v-layout>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
      click: 0,
      sectionHeader: [{
          text: 'About Me',
          icon: 'person'
        },
        {
          text: 'Resume',
          icon: 'assessment'
        },
        {
          text: 'Portfolio',
          icon: 'description'
        }
      ],
      experiences: [{
          title: 'Software Engineer',
          company: 'CytoSmart Technologies,BV',
          location: 'Eindhoven, Netherlands',
          date: 'Feb 2019 - Present',
          description: [
            'Developed a tracking system for the process in the cloud',
            'Added features to make the application to load faster',
            'Based on ASP .NET MVC, ASP .NET Core, HTML + CSS, Vue.js, and Azure Cloud Services'
          ],
          imageLink: require('@/assets/images/nda.jpg'),
          color: "indigo",

        },
        {
          title: 'Software Developer',
          company: 'Fontys Hogescholen',
          location: 'Eindhoven, Netherlands',
          date: 'Sep 2018 - Jan 2019',
          description: [
            'Developed an administrator panel for Fontys Alumni portal',
            'Added Content Management Features for the portal',
            'Based on PHP Laravel, HTML + CSS, and jQuery'
          ],
          imageLink: require('@/assets/images/faw.png'),
          color: "purple",

        },
        {
          title: 'Software Developer',
          company: 'Aneka Cipta Total Solusindo,PT',
          location: 'Surabaya, Indonesia',
          date: 'Dec 2017 - Mar 2018',
          description: [
            'Developed Business trip & Leave Managament System',
            'Added Report Genera  tor modules',
            'Based on PHP, HTML + CSS, and jQuery'
          ],
          imageLink: require('@/assets/images/acs.png'),
          color: "orange",

        },

      ],


      education: [{
          title: 'Bachelor of Computer Science',
          place: 'Fontys University of Applied Sciences',
          location: 'Eindhoven, Netherlands',
          date: 'Sep 2019 - Present',
          color: "purple",
        },
        {
          title: 'Bachelor of Computer Science',
          place: 'Petra Christian University',
          location: 'Surabaya, Indonesia',
          date: 'Aug 2015 - Present',
          color: "blue",

        }

      ],
      techskills: [{
          skill: 'ASP .NET MVC',
          color: 'blue'
        },
        {
          skill: 'ASP .NET Core',
          color: 'blue'
        },
        {
          skill: 'Entity Framework',
          color: 'blue'
        },
        {
          skill: 'C#',
          color: 'blue'
        },
        {
          skill: 'Microsoft Azure',
          color: 'blue'
        },
        {
          skill: 'SQL',
          color: 'gray'
        },
        {
          skill: 'NoSQL',
          color: 'gray'
        },
        {
          skill: 'HTML',
          color: 'purple'
        },
        {
          skill: 'CSS',
          color: 'purple'
        },
        {
          skill: 'Bootstrap',
          color: 'purple'
        },
        {
          skill: 'Javascript',
          color: 'green'
        },
        {
          skill: 'Vue.js',
          color: 'green'
        },
        {
          skill: 'jQuery',
          color: 'green'
        },
        {
          skill: 'PHP',
          color: 'orange'
        },
        {
          skill: 'Laravel',
          color: 'orange'
        },
        {
          skill: 'Python',
          color: 'light-green'
        },
        {
          skill: 'Flask',
          color: 'light-green'
        },
        {
          skill: 'Java',
          color: 'teal'
        },
        {
          skill: 'Android',
          color: 'teal'
        },
      ],
      softskills: [{
          skill: 'Full stack Web Development',
          color: 'blue'
        },
        {
          skill: 'Cloud Development',
          color: 'light-blue'
        },
        {
          skill: 'Mobile Development',
          color: 'green'
        },
        {
          skill: 'Agile',
          color: 'pink'
        },
        {
          skill: 'Object Oriented Programming',
          color: 'teal'
        },

        {
          skill: 'RESTful Web Services',
          color: 'amber'
        },
      ],
      traits: [{
          skill: 'Critical',
          color: 'red'
        },
        {
          skill: 'Curious',
          color: 'blue'
        },
        {
          skill: 'Dedicated',
          color: 'green'
        },
        {
          skill: 'Honest',
          color: 'amber'
        },
        {
          skill: 'Straight-forward',
          color: 'pink'
        },
      ],
      portfolio: [{
          name: 'Job Management System',
          img: []
        },
        {
          name: 'Fontys Alumni Portal',
          img: [
            require('@/assets/images/faw.png'),
            require('@/assets/images/faw-1.png'),
            require('@/assets/images/faw-2.png'),

          ]
        },
        {
          name: 'Business Trip & Leave Management System',
          img: [
            require('@/assets/images/acs.png'),
            require('@/assets/images/acs-1.png'),
            require('@/assets/images/acs-2.png'),

          ]
        },
        {
          name: 'Petra Tax Major Website',
          img: [
            require('@/assets/images/pp.png'),
            require('@/assets/images/pp-1.png'),
            require('@/assets/images/pp-2.png'),

          ]
        },

      ]

    }),

  }

</script>

<style>

</style>
