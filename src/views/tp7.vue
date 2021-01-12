<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>tp7</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>
    
      <ion-list>

        <ion-item-sliding >
          <ion-item :key="dbitem.id" v-for="dbitem in db">
            <ion-label v-if="!dbitem.donne">{{dbitem.text}}</ion-label>
            <ion-label v-if="dbitem.donne" style="background-color:red">{{dbitem.text}}</ion-label>
            <ion-checkbox @click="underline(dbitem)" slot="start"></ion-checkbox>
            <ion-button slot="end" @click="supprime(dbitem)">supprime</ion-button>
          </ion-item>
        </ion-item-sliding>
      </ion-list>
      <ion-item id="button" >
        <ion-input   v-model="addtext"></ion-input>
        <ion-button slot="end" @click="add()">add</ion-button>
      </ion-item>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar,IonList,IonItem,IonLabel,IonInput,
IonItemSliding,IonCheckbox } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Home',
  
  data(){
    return {
      addtext:"",
      compter: 0,
      db:[] as any,
    }
  },
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,IonInput,
    IonToolbar,IonList,IonItem,IonLabel,IonItemSliding,IonCheckbox
  },methods:{
    supprime(obj: any){
      this.db.splice(this.db.indexOf(obj),1);
    },
    underline(obj: any){
        this.db[this.db.indexOf(obj)].donne=!obj.donne;

    },
    add(){
      this.compter ++;
      this.db.push({
        id: this.compter,
        text: this.addtext,
        donne: false
      });
      this.addtext="";
    }
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
#button{
    position: fixed;
    left: 0;
    bottom: 10px;
    right: 0;
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