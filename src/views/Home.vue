<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>tp6</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
    
      <ion-item>
        <ion-label>Gender</ion-label>
        <ion-select v-model="Gender" placeholder="Select One">
          <ion-select-option value="Mm">Female</ion-select-option>
          <ion-select-option value="Mr">Male</ion-select-option>
        </ion-select>
      </ion-item>
      <ion-item>
          <ion-label position="fixed">Nom</ion-label>
          <ion-input v-model="nom"></ion-input>
        </ion-item>
        <ion-item>
          <ion-label position="fixed">Prénom</ion-label>
          <ion-input v-model="prenom"></ion-input>
        </ion-item>
        <ion-item>
          <ion-label>Date de naissance</ion-label>
          <ion-datetime v-model="date" display-format="YYYY-MM-DD"></ion-datetime>
        </ion-item>
          <ion-list>
    <ion-radio-group v-model="specialite">
      <ion-list-header>
        <ion-label>
          Spécialité
        </ion-label>
      </ion-list-header>

      <ion-item>
        <ion-label>Informatique</ion-label>
        <ion-radio value="Informatique"></ion-radio>
      </ion-item>

      <ion-item>
        <ion-label>Électrique</ion-label>
        <ion-radio value="Électrique"></ion-radio>
      </ion-item>

      <ion-item>
        <ion-label>Mécanique</ion-label>
        <ion-radio value="Mécanique"></ion-radio>
      </ion-item>

      <ion-item>
        <ion-label>Gestion</ion-label>
        <ion-radio value="Gestion"></ion-radio>
      </ion-item>
    </ion-radio-group>
  </ion-list>

      <ion-button @click="show()" expand="full">Full Button</ion-button>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar ,IonButton,alertController ,IonSelect,  IonItem, IonInput,
  IonLabel, 
  IonList,
  IonDatetime,
  IonListHeader, 
  IonRadio, 
  IonRadioGroup } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Home',
  methods:{
    show(){
      let text: any;
      if(this.Gender!=null ||this.Gender != ""){
        text = this.Gender+" ";
      }else{
        return;
      }
      if(this.nom!=null ||this.nom != ""){
        text += this.nom+" ";
      }else{
        return;
      }
       if(this.prenom!=null ||this.prenom != ""){
        text += this.prenom+" ";
      }else{
        return;
      }
       if(this.date!=null ||this.date != ""){
        text += "nee en "+this.date.substring(0,10)+" ";
      }else{
        return ;
      }
      if(this.specialite!=null ||this.specialite != ""){
        text += "specialite : "+this.specialite;
      }else{
        return;
      }
      this.alert(text,"merci :D");
    },
    async alert(text: string, header: string) {
      const alert = await alertController
        .create({
         
          header: header,
          message: text,
          buttons: ['OK'],
        });
      return alert.present();
    },
  },
  data(){
    return {
      nom:null,
      prenom:null,
      date:"",
      Gender:null,
      specialite: null
    }
  },
  components: {
    IonInput,
    IonContent,
    IonHeader,
    IonPage,IonButton,
    IonTitle,
    IonToolbar,
    IonItem, 
    IonLabel, 
    IonList, 
    IonListHeader, 
    IonRadio, 
    IonDatetime,
    IonRadioGroup,
    IonSelect
  }
});
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>