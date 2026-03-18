
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
          :error-text="erroTarefa"
          :class="{ 'ion-invalid ion-touched': erroTarefa }"
        />

        <IonButton
          expand="block"
          color="primary"
          fill="solid"
          @click="adicionarTarefa"
        >
          <IonIcon :icon="addOutline" slot="start"/>
          Adicionar
        </IonButton>

      </IonCardContent>
    </IonCard>

    <!-- CARD LISTA -->
    <IonCard>

      <IonCardHeader>
        <IonCardTitle>
          Minhas Tarefas ({{ tarefas.length }})
        </IonCardTitle>
      </IonCardHeader>

      <IonCardContent>

        <p v-if="!tarefas.length" class="ion-text-center ion-padding">
          Nenhuma tarefa cadastrada.
        </p>

        <IonList v-else>

          <IonItem
            v-for="(t, i) in tarefas"
            :key="i"
          >
            <IonIcon
              slot="start"
              :icon="checkmarkCircleOutline"
            />

            <IonLabel>
              {{ t }}
            </IonLabel>

            <IonButton
              slot="end"
              fill="clear"
              color="danger"
              @click="removerTarefa(i)"
            >
              <IonIcon :icon="trashOutline"/>
            </IonButton>

          </IonItem>

        </IonList>

      </IonCardContent>

    </IonCard>

  </IonContent>

</IonPage>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonList,
  IonItem,
  IonLabel,
  IonInput,
  IonButton,
  IonIcon,
  IonCard,
  IonCardHeader,
  IonCardTitle,
  IonCardContent
} from "@ionic/vue";

import { addOutline, trashOutline, checkmarkCircleOutline } from "ionicons/icons";

const novaTarefa = ref("");
const tarefas = ref<string[]>([]);

const erroTarefa = computed(() =>
  !novaTarefa.value.trim() ? "Campo obrigatório" : ""
);

const adicionarTarefa = () => {
  if (!novaTarefa.value.trim()) return;

  tarefas.value.push(novaTarefa.value);
  novaTarefa.value = "";
};

const removerTarefa = (index: number) => {
  tarefas.value.splice(index, 1);
};
</script>