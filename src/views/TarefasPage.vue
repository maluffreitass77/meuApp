<template>
<IonPage>

  <IonHeader>
    <IonToolbar>
      <IonTitle>Mini App de Tarefas</IonTitle>
    </IonToolbar>
  </IonHeader>

  <IonContent class="ion-padding">

    <!-- CARD NOVA TAREFA -->
    <IonCard>
      <IonCardHeader>
        <IonCardTitle>Nova Tarefa</IonCardTitle>
      </IonCardHeader>

      <IonCardContent>

        <IonInput
          label="Nome da tarefa"
          label-placement="floating"
          v-model="novaTarefa"
          placeholder="Ex: Estudar Vue.js"
          :clear-input="true"
        />

        <IonButton
          expand="block"
          color="primary"
          @click="adicionarNova"
        >
          <IonIcon :icon="addOutline" slot="start"/>
          Adicionar
        </IonButton>

      </IonCardContent>
    </IonCard>

    <!-- BUSCA -->
    <IonCard>
      <IonCardContent>
        <IonInput
          v-model="busca"
          placeholder="Buscar tarefa..."
        />
      </IonCardContent>
    </IonCard>

    <!-- CARD LISTA -->
    <IonCard>

      <IonCardHeader>
        <IonCardTitle>
          Minhas Tarefas ({{ filtradas.length }})
        </IonCardTitle>
      </IonCardHeader>

      <IonCardContent>

        <p v-if="!filtradas.length" class="ion-text-center ion-padding">
          Nenhuma tarefa encontrada.
        </p>

        <div v-else>
          <CardTarefa
            v-for="t in filtradas"
            :key="t.id"
            :tarefa="t"
            @remover="remover"
            @concluir="concluir"
          />
        </div>

      </IonCardContent>

    </IonCard>

  </IonContent>

</IonPage>
</template>

<script setup lang="ts">
import { ref } from "vue";

import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonInput,
  IonButton,
  IonIcon,
  IonCard,
  IonCardHeader,
  IonCardTitle,
  IonCardContent
} from "@ionic/vue";

import { addOutline } from "ionicons/icons";

// ✅ IMPORTS NOVOS
import { useTarefas } from "../composables/useTarefas";
import CardTarefa from "../components/CardTarefa.vue";

// ✅ COMPOSABLE
const {
  busca,
  filtradas,
  adicionar,
  remover,
  concluir
} = useTarefas();

// INPUT
const novaTarefa = ref("");

// FUNÇÃO ADD
function adicionarNova() {
  adicionar(novaTarefa.value);
  novaTarefa.value = "";
}
</script>