<template>
  <div class="q-pa-lg">
    <div class="q-gutter-y-lg" style="max-width: 750px" >
      <q-card>
        <q-tabs
          v-model="tab"
          dense
          class="text-grey"
          active-color="primary"
          indicator-color="primary"
          align="justify"
          narrow-indicator
        >
          <q-tab name="symptoms" label="Symptoms"/>
          <q-tab name="record" label="Record"/>
        </q-tabs>

        <q-separator/>

        <q-tab-panels v-model="tab" animated height="5000">
          <q-tab-panel name="symptoms" height="5000">
            <q-form>
              <div class="text-h6">Symptoms</div>

              <div class="row">
                <div class="col">
                  <q-input outlined v-model="symptom" label="Symptom" style="max-width: 300px"/>
                </div>
                <div class="col">
                  <q-btn @click="addSymptom()" color="white" text-color="black" label="Add"/>
                </div>
              </div>


              <div class="q-pa-lg" style="max-width: 300px">
                <q-input ref="symptomsTextArea"
                         v-model="symptomList"
                         filled
                         type="textarea"
                         autogrow
                         rows="4" cols="35"

                />


                <!--                    <q-list bordered separator ref="symptomListDisplay">-->

                <!--                      <q-item clickable v-for="symptom in getSymptoms()" :key="symptom.label">-->

                <!--                        <q-item-section>{{symptom.label}}</q-item-section>-->

                <!--                      </q-item>-->
                <!--                    </q-list>-->

              </div>


            </q-form>
          </q-tab-panel>

          <q-tab-panel name="record">
            <div class="text-h6">Record</div>
            <q-form>

              <div class="q-pa-lg" style="max-width: 300px">

                <q-input ref="location"
                         label="Location"
                         filled
                         type="text"
                         autogrow
                         v-model="location"

                />
              </div>


              <div class="q-pa-lg" style="max-width: 300px">
                <q-input ref="activity"
                         label="Activity"
                         filled
                         type="text"
                         autogrow
                         v-model="activity"

                />
              </div>

              <div class="q-pa-lg" style="max-width: 750px">
                <div class="row q-col-gutter-lg">
                  <div class="col" >
                    <q-select outlined v-model="symptomInstances1" :options=getSymptoms()></q-select>
                  </div>

                  <div class="col-5">
                    <q-slider
                      v-model="howBadIsIt1"
                      :min="0"
                      :max="10"
                      :step="1"
                      label
                      label-always
                      color="light-green"
                      marker-labels
                    />
                  </div>
                  <div class="col">
                    <q-btn  @click="rowVisible = true" color="primary" size="sm" round icon="eva-plus-circle" />



                  </div>




                </div>

              </div>

              <div v-if="rowVisible" class="q-pa-lg" style="max-width: 750px">
                <div class="row q-col-gutter-lg">
                  <div class="col" >
                    <q-select outlined v-model="symptomInstances2" :options=getSymptoms()></q-select>
                  </div>

                  <div class="col-5">
                    <q-slider
                      v-model="howBadIsIt2"
                      :min="0"
                      :max="10"
                      :step="1"
                      label
                      label-always
                      color="light-green"
                      marker-labels
                    />
                  </div>
                  <div class="col">
                    <q-btn  @click="rowVisible = true" color="primary" size="sm" round icon="eva-plus-circle" />



                  </div>




                </div>

              </div>
              <q-separator/>
              <q-btn @click="submit()" color="primary" label="Submit" />

            </q-form>
          </q-tab-panel>

        </q-tab-panels>
      </q-card>


    </div>
  </div>
</template>

<script>
import {ref} from 'vue'

export default {

  setup() {

    return {

      tab: ref('symptoms'),
      symptom: "",

      selectedCategory: null,



    }
  },
  data(){
    return {
      symptomInstances1: [],
      symptomInstances2: [],
      howBadIsIt1: [],
      howBadIsIt2: [],
      location: "",
      activity: "",
      symptomList: [],
      rowVisible:false
    }
  },
  methods: {
    addSymptom() {
      console.log(this.symptom)
      //this.$refs.symptomListDisplay.refresh()
      this.symptomList.push(this.symptom)
      console.log(this.symptomList.length)
    },
    getSymptoms() {
      console.log(this.symptomList.length)
      return this.symptomList;
    },
    addInstanceRow(){
      console.log("add instance row")
    },
    submit(){
      console.log("submit")
    }
  }
}
</script>
