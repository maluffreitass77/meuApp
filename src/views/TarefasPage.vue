<template>
<ion-page>

<ion-header>
  <ion-toolbar>

    <ion-buttons slot="start">
      <ion-back-button default-href="/" />
    </ion-buttons>

    <ion-title>Tarefas</ion-title>

  </ion-toolbar>
</ion-header>

<ion-content class="ion-padding">

  <!-- Campo para nova tarefa -->

  <ion-item>
    <ion-input
      v-model="novaTarefa"
      placeholder="Digite uma tarefa">
    </ion-input>
  </ion-item>

  <ion-button expand="block" @click="adicionarTarefa">
    Adicionar
  </ion-button>

  <!-- Estado vazio -->

  <p v-if="tarefas.length === 0">
    Nenhuma tarefa cadastrada. Adicione a primeira!
  </p>

  <!-- Lista de tarefas -->

  <ion-list v-else>

    <ion-item v-for="(tarefa, index) in tarefas" :key="index">

      <ion-label>
        {{ tarefa }}
      </ion-label>

      <ion-button
        color="danger"
        fill="clear"
        @click="removerTarefa(index)">
        Remover
      </ion-button>

    </ion-item>

  </ion-list>

</ion-content>

</ion-page>
</template>

<script setup lang="ts">
import {
IonPage,
IonHeader,
IonToolbar,
IonTitle,
IonContent,
IonItem,
IonInput,
IonButton,
IonList,
IonLabel,
IonButtons,
IonBackButton
} from '@ionic/vue'

import { ref } from 'vue'

const novaTarefa = ref('')
const tarefas = ref<string[]>([])

const adicionarTarefa = () => {

  if (novaTarefa.value.trim() === '') return

  tarefas.value.push(novaTarefa.value)

  novaTarefa.value = ''
}

const removerTarefa = (index:number) => {
  tarefas.value.splice(index, 1)
}
</script>