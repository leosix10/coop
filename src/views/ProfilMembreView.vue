<script setup>
import { useMembresStore } from '@/stores/membres'
import { onMounted } from 'vue';
import { useRouter } from 'vue-router';
import { ref } from 'vue';

// const membresStore = inject('membres');
const membresStore = useMembresStore();
const router = useRouter();

let membre = ref({});

onMounted(() => {
    const id = router.currentRoute.value.params.id;
    membre.value = membresStore.getMembre(id);
    console.log(membre);
})
</script>

<template>
    <div>
        <h1 class="title">Informations relatives au compte selectionné</h1>
        <p><b>Nom prénom :</b> {{ membre.fullname }}</p>
        <p><b>Email :</b> {{ membre.email }}</p>
        <p><b>Date de création :</b> {{ membre.created_at }}</p>
    </div>
</template>