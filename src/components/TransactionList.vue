<template>
    <h3>History</h3>
        <ul id="list" class="list">
            <li v-for="transaction in transactions"v-bind:key="transaction.id" v-bind:class="transaction.amount > 0 ? 'plus' : 'minus'">
                {{ transaction.text }} <span>${{ transaction.amount }}</span>
                <button class="delete-btn">x</button>
            </li>
        </ul>
</template>

<script setup>
    import { defineProps } from 'vue';
    const props = defineProps({
        transactions: {
            type: Array,
            required: true,
        },
    })
</script>