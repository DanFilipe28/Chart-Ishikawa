<template>
   <v-col  cols="12">
      <v-row class="">
         <v-col cols="12">
           
            <div class="block-cima"> 
              <div class="separator"/>
               <div> 
                  <div class="linha-quadro ">
                     <div>
                      <v-col 
                           <!-- bloco que  recebe input de dados -->
                        >
                           <v-text-field
                              v-model=""
                              readonly
                              dense
                              rounded
                              class="float-left"

                           ></v-text-field>
                        </v-col > 

                     </div>
                  </div>
               </div>
            
               <div>
                  <div  class="linha-quadro">
                    <v-col 
                           <!-- bloco que  recebe input de dados -->
                        >
                           <v-text-field
                              v-model=""
                              readonly
                              dense
                              rounded
                              class="float-left"
                           ></v-text-field>
                        </v-col > 
                  </div>
               </div>

               <div>
                  <div class="linha-quadro">
                      <v-col 
                            <!-- bloco que  recebe input de dados -->
                        >
                           <v-text-field
                              v-model=""
                              readonly
                              dense
                              rounded
                              class="float-left"
                           ></v-text-field>
                        </v-col > 
                     </div>
               </div>

               <div>
                  <div class="linha-quadro">
                      <v-col 
                            <!-- bloco que  recebe input de dados -->
                        >
                           <v-text-field
                              v-model=""
                              readonly
                              dense
                              rounded
                              class="float-left"
                           ></v-text-field>
                        </v-col > 
                     </div>
               </div>
              <div class="separator"/>
              <div class="separator"/>
              <div />

               </div>
               

         </v-col>
         <!-- FIM DO BLOCO DE CIMA  -->

       <!-- BLOCO DO MEIO DE ISHIKAWA-->

        <v-col cols="11"></v-col>  
        <v-col cols="1">
              <div>
                  <div>
                      <div id="linha-Problema">
                           <!-- Bloco Problema onde vai ser o tema do Chart -->
                       <v-textarea 
                           readonly 
                           auto-grow
                           rounded
                           filled
                           v-model=""
                        ></v-textarea>
                      </div>
                  </div>
              </div> 
        </v-col>
      <!-- FIM DO BLOCO DO MEIO -->
        
        <!-- BLOCO DE BAIXO DO ISHIKAWA -->
        <v-col cols="12">
         <div class="block-baixo">
           <div />
              <div>
                  <div  class="linha-quadro">
                      <v-col 
                           <!-- bloco que  recebe input de dados -->
                        >
                          <v-text-field
                              v-model=""
                              readonly
                              dense
                              rounded
                              class="float-left"
                          ></v-text-field>
                        </v-col > 
                  </div>
              </div>
              <div>
                <div class="linha-quadro">
                    <v-col 
                         <!-- bloco que  recebe input de dados -->
                      >
                        <v-text-field
                            v-model=""
                            readonly
                            dense
                              rounded
                              class="float-left"
                        ></v-text-field>
                      </v-col > 
                </div>
            </div>

              <div>
                <div class="linha-quadro">
                    <v-col 
                         <!-- bloco que  recebe input de dados -->
                      >
                        <v-text-field
                            v-model="values.value"
                            readonly
                            dense
                              rounded
                              class="float-left"
                        ></v-text-field>
                      </v-col > 
                </div>
              </div>

            <div>
               <div class="linha-quadro">
                  <v-col 
                         <!-- bloco que  recebe input de dados -->
                    >
                        <v-text-field
                          v-model=""
                          readonly
                          dense
                          rounded
                          class="float-left"
                        ></v-text-field>
                    </v-col > 
               </div>
            </div>

            <div />
            <div />
            <div />
           
          </div> 
        </v-col>
        
    </v-row>
  </v-col>
</template>

<script>
export default {
  props: {
    document: {
      required: true,
      type: Object,
    },
  },
  components: {},
  data: () => ({
    itemMethod: [],
    itemMeasurement: [],
    itemMaterial: [],
    itemManegement: [],

    itemMachine: [],
    itemEviroment: [],
    itemManpower: [],
    itemMaintenance: [],

    indexMethod: [],
    indexMeasurement: [],
    indexMaterial: [],
    indexManegement: [],

    indexMachine: [],
    indexEviroment: [],
    indexManpower: [],
    indexMaintenance: [],
  }),
  mounted() {
    this.document.map((item) => {
      if (item.title == 'Categoria') {
        item.values.map((itemCateg, i) => {
          if (itemCateg.value == 'Method') {
            this.indexMethod.push(i);
          }
          if (itemCateg.value == 'Material') {
            this.indexMaterial.push(i);
          }
          if (itemCateg.value == 'Management') {
            this.indexManegement.push(i);
          }
          if (itemCateg.value == 'Machine') {
            this.indexMachine.push(i);
          }
          if (itemCateg.value == 'Eviroment') {
            this.indexEviroment.push(i);
          }
          if (itemCateg.value == 'Manpower') {
            this.indexManpower.push(i);
          }
          if (itemCateg.value == 'Maintenance') {
            this.indexMaintenance.push(i);
          }
          if (itemCateg.value == 'Measurement') {
            this.indexMeasurement.push(i);
          }
        });
      }
    });

    this.document.map((item) => {
      if (item.title == 'Sugestão / Ideia') {
        for (let i = 0; i < this.indexMaterial.length; i++) {
          this.itemMaterial.push(item.values[this.indexMaterial[i]]);
        }
        for (let i = 0; i < this.indexManegement.length; i++) {
          this.itemManegement.push(item.values[this.indexManegement[i]]);
        }
        for (let i = 0; i < this.indexMachine.length; i++) {
          this.itemMachine.push(item.values[this.indexMachine[i]]);
        }
        for (let i = 0; i < this.indexEviroment.length; i++) {
          this.itemEviroment.push(item.values[this.indexEviroment[i]]);
        }
        for (let i = 0; i < this.indexManpower.length; i++) {
          this.itemManpower.push(item.values[this.indexManpower[i]]);
        }
        for (let i = 0; i < this.indexMaintenance.length; i++) {
          this.itemMaintenance.push(item.values[this.indexMaintenance[i]]);
        }
        for (let i = 0; i < this.indexMethod.length; i++) {
          this.itemMethod.push(item.values[this.indexMethod[i]]);
        }
        for (let i = 0; i < this.indexMeasurement.length; i++) {
          this.itemMeasurement.push(item.values[this.indexMeasurement[i]]);
        }
      }
    });
  },
};
</script>

