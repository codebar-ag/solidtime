<script setup lang="ts">
import MultiselectDropdown from '@/packages/ui/src/Input/MultiselectDropdown.vue';
import { storeToRefs } from 'pinia';
import type { Client } from '@/packages/api/src';
import { useClientsStore } from '@/utils/useClients';

const clientsStore = useClientsStore();
const { clients } = storeToRefs(clientsStore);

function getKeyFromItem(item: Client) {
    return item.id;
}

function getNameForItem(item: Client) {
    return item.name;
}
</script>

<template>
    <MultiselectDropdown
        search-placeholder="Search for a Client..."
        :items="clients"
        :get-key-from-item="getKeyFromItem"
        :get-name-for-item="getNameForItem">
        <template #trigger>
            <slot name="trigger"></slot>
        </template>
    </MultiselectDropdown>
</template>
