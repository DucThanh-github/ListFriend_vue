<!-- <template> -->
    <!-- <div>
        name: {{ user.name }} 
        <br/>
        age: {{ user.age }}
     </div> -->
    <!-- <input :value="user.name" @input="changeName"/>
    <input :value="user.age" @input="changeAge"/> -->
    <!-- <input type="number" v-model="soluonghang">
    <button @click="uploadHang">Click</button> -->
    <!-- <input type="number" :value="soluonghang" @input="changInput"/>

</template>

<script lang="ts">
import { PropType } from 'vue'


interface User {
    name: string,
    age: string
}

// export default (await import('vue')).defineComponent({
    name: 'friend-oh',
    props: {
        user: {
            validator(value: User) {
                console.error('ten duoi 5 ki tu')
                return value.name.length < 5
            }, 
            type: Object as PropType<User>,
            required: true
        },
        hanhDong: {
            type: Function as PropType<(soluong:number)=>void>,
            required: true
        }
        
    },
    data() {
        return {
            isFavorted: false,
            soluonghang: 0
        }
    },
    methods: {
        uploadHang() {
            if (this.soluonghang <= 0) {
                console.log('so luong hang chua du')
            } else {
                this.hanhDong(this.soluonghang)
            }
        },
        changeName(ev: Event) {
            this.$emit('update:user', {
                name: (ev.target as HTMLInputElement).value,
                age: this.user.age
            })
        },
        changeAge(ev: Event) {
            this.$emit('update:user', {
                age: (ev.target as HTMLInputElement).value,
                name: this.user.name
            })
    }}
})
</script> -->