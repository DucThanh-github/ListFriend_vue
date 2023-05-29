<template>
    <div style="margin: 10px 0 10px;">
        <input type="text" :value="modelValue.name" @input="changName">
        <input type="number" :value="modelValue.age" @input="changAge">
        <span name="span" v-if="isLike">LIKE</span>
        <button @click="toggleLike">{{ isLike? "Unlike": "Like" }}</button>
        <button @click="$emit('deleleFriend',modelValue.id)">Delete</button>
        
    </div>
    
</template>

<script lang="ts">
import { PropType } from 'vue';

interface User {
    id: number;
    name: string;
    age: number;
}
export default (await import('vue')).defineComponent({
props: {
    modelValue : {
        type: Object as PropType<User>,
        required: true
    }
},
data() {
    return {
        isLike: false
    }
},
methods: {
    changName(ev:Event) {
            this.$emit('update:modelValue', {
                id:this.modelValue.id,
                name: (ev.target as HTMLInputElement).value,
                age: this.modelValue.age
            })
    },
    changAge(ev:Event) {
        this.$emit('update:modelValue', {
                id:this.modelValue.id,
                name: this.modelValue.name,
                age: (ev.target as HTMLInputElement).value
            })
        
    },
    toggleLike() {
        this.isLike = !this.isLike
    }
}
})
</script>