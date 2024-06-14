<template>
    <h3>Add Transaction</h3>
    <form id="form">
        <div class="form-control">
            <label for="text">Text</label>
            <input type="text" id="text" placeholder="Enter text..."/>
        </div>
        <div class="form-control">
            <label for="amount">amount
                <br /> (negative - expense, positive - income)
            </label>
            <input type="number" id="amount" placeholder="Enter amount..."/>
        </div>
        <button class="btn">Add Transaction</button>
    </form>
</template>
<script setup>
import { ref } from 'vue';
import {useToast} from 'vue-toastification';
const toast = useToast();

const text = ref('');

const amount = ref('');

const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
    if (!text.value || !amount.value){
        toast.error('Both fields must be filled');
        return;
    }


    const transactionData = {
        text: text.value,
        amount: parseFloat(amount.value)
    }
    emit('transactionSubmitted', transactionData);
    text.value = '';
    amount.value = '';
};

</script>