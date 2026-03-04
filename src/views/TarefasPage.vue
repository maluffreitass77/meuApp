<template>
  <IonPage>
    <IonHeader>
      <IonToolbar>
        <IonTitle>Tarefas</IonTitle>
      </IonToolbar>
    </IonHeader>

    <IonContent class="ion-padding">
      <p>Minha nova página de tarefas 🚀</p>
    </IonContent>
  </IonPage>
</template>

<script setup lang="ts">
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent
} from '@ionic/vue'
</script>

<style scoped>
p {
  font-size: 18px;
}
</style>