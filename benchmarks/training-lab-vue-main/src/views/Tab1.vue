<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 1</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <div>Logged in: {{ currentUser ? 'Yes' : 'No' }}</div>
      <div v-if="currentUser">
        <div>User: {{ currentUser?.email }}</div>
      </div>

      <ion-button :disabled="!currentUser" @click="logout">Logout</ion-button>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonButton,
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
} from '@ionic/vue';
import { ref } from 'vue';
import { User } from '@/models';
import { useRouter } from 'vue-router';

export default {
  name: 'Tab1',
  components: {
    IonButton,
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
  },
  setup() {
    const currentUser = ref<User>();
    const router = useRouter();

    const logout = () => {
      router.replace('/login');
    };

    return { currentUser, logout };
  },
};
</script>
