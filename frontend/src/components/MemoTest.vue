<template>
    <div class="memo">
        <div class="act">
            <button class="btn btn-primary" @click="add()">추가</button>
        </div>
        <ul>
            <li v-for="d in state.data" :key="d.id" @click="edit(d.id)">{{d.content}}</li>
        </ul>
    </div>
</template>
<script>
import {reactive} from "vue"
import axios from "axios"

export default {
    setup() {
        
        const state = reactive({
            data :[],
        });


        const add=()=>{
            const content = prompt("입력하라");
            if(!content) {
                alert('입력해');
                return add();
            }
            // state.data.push("추가 내용");
            axios.post("/api/memos", {content}).then((res)=>{
                state.data = res.data;
            })
        };

        const edit = (id) =>{
            const content = prompt("입력해라", state.data.find(d=>d.id == id).content);
            console.log(content);
            axios.put("/api/memos/" + id, {content}).then((res) => {
                state.data = res.data;
            })
        }


        axios.get("/api/memos").then((res) =>{
            state.data = res.data;
        });

        return {state, add, edit};
    },
}
</script>

<style lang="scss" scoped>
    .momo {
        .act{ 
            padding:10px 10px 5px 5px;
            text-align: right;
        }
        ul{ 
            border-top: 1px;
            list-style: none;
            padding:15px 0;
            margin:0;

            li{ 
                padding:5px 10px;
                margin:5px;
            }
        }
    }
</style>