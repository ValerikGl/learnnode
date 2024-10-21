<script setup>
import { ref } from 'vue';

    let joke = ref('');
    let response = await fetch('https://api.chucknorris.io/jokes/random');
    let data = await response.json();
    console.log(data);
    joke = data.value;
</script>

<template>
<div class="container">
    <div class="content has-text-centered">
        <h1>{{ joke }}</h1>
    </div>
</div>

</template>