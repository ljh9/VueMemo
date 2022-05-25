<template>
    <div class="memo">
        <div class="act">
            <button class="btn btn-primary" @click="add()">추가</button>
        </div>
        <ul>
            <li v-for="(d, idx) in state.data" :key="idx">{{d}}</li>
        </ul>
    </div>
</template>
<script>
import {reactive} from "vue"
import {axios} from "axios"

export default {
    setup() {
        
        const state = reactive({
            data :["메모 1 내용", "메모 2 내용", "메모 3 내용", "메모 4 내용", "메모 5 내용"],
        });
        const add=()=>{
            state.data.push("추가 내용");
        };
        axios.get("/api/memos").then((res) =>{
            console.log(res.data);
        });

        return {state, add};
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