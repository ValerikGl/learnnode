<script setup>
import { computed } from 'vue';
let props = defineProps({
    color:{
    primary: 
    String,
    required:false,
    validator(value, props) {
        return [
        'primary',
        'link',
        'info',
        'success',
        'warning',
        'danger',
        'white',
        'light',
        'dark',
        'text',
        'ghost',
        ].includes(value);
    }
    },
    light: {
        type: Boolean,
        required: false,
    }
});

let classNames = computed(( ) => {
    let names = [];
    if(props.color){
        names.push('is-' + props.type);
    }
    if(light){
        names.push('is-light');
    }
    console.log(props);
    return names.join('');
})
</script>

<template>
  
    <button class="button" :class="'is-'+type">
        <slot></slot>
    </button>
</template>