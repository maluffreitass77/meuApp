<template>
<ion-page>

<ion-header>
  <ion-toolbar>
    <ion-title>Gerenciador de Tarefas</ion-title>
  </ion-toolbar>
</ion-header>

<ion-content class="ion-padding">

  <h2>Bem-vindo!</h2>
  <p>Este aplicativo permite adicionar e organizar suas tarefas.</p>

  <ion-button expand="block" @click="irParaTarefas">
    Ir para Tarefas
  </ion-button>

</ion-content>

</ion-page>
</template>

<script setup lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButton } from '@ionic/vue'
import { useIonRouter } from '@ionic/vue'

const router = useIonRouter()

const irParaTarefas = () => {
  router.push('/tarefas')
}
</script>