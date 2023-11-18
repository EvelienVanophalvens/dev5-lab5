<script setup>
    //import ref
    import { ref, reactive, onMounted } from 'vue'



    let message = ref(""); //int, string, boolean
    let allMessages = reactive({
        data: ["heel", "even", "simpel", "doen"],
    }); //array, object

    onMounted(() => {
        fetch("https://lab4-716k.onrender.com/api/v1/messages")
            .then((response) => response.json())
            .then((data) => {
                allMessages.data = data["data"][0];
            });
    });


    function sendMessage() {
        allMessages.data.push(message.value);
        message.value = "";
    }

</script>

<template>
    <ul>
        <li v-for="m in allMessages.data">{{ m["text"] }}</li>
    </ul>

    <div>
        <input v-model="message" type="text" placeholder="Type your message here">
        <button @click="sendMessage">Send</button>
    </div>
</template>

<style scoped>

</style>
