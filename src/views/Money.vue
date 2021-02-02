
<template>

    <Layout class-prefix="layout">
     
        <NumberPad :value.sync="record.amount" @submit="saveRecord"></NumberPad>
        <Types :value.sync="record.type"></Types>
        <Notes 
              fieldName="备注"
              placeholder="在这里输入备注"
              @update:value="onUpdateNotes"></Notes>
        <Tags :dataSource.sync="tags" @update:value="onUpdateTags"></Tags>
   
    </Layout>        

</template>

<script lang="ts">
    import NumberPad from '@/components/Money/NumberPad.vue';
    import Types from '@/components/Money/Types.vue';
    import Notes from '@/components/Money/Notes.vue';
    import Tags from '@/components/Money/Tags.vue';

    import Vue from 'vue';
    import { Component, Watch } from 'vue-property-decorator';
    import recordListModel  from '@/models/recordListModel';
    
   

    const recordList = recordListModel.fetch();
    
  

    @Component({

        components: {Tags, Notes, Types, NumberPad},

    })


    export default class Money extends Vue{
       
        tags = window.tagList;
        recordList: RecordItem[] = recordList;

        record: RecordItem = {
            tags:[], notes: '', type:'-', amount: 0
        }
        onUpdateTags(value: string[]) {
            this.record.tags = value;
        }
        onUpdateNotes(value: string) {
            this.record.notes = value;
        }

        saveRecord(){
            recordListModel.create(this.record);

        }

        @Watch('recordList')

        onRecordListChannge() {
           recordListModel .save();
        }
       
        
        
    }
</script>
<style lang="scss">
    .layout-content {
        
        display: flex;
        flex-direction: column-reverse;


    }

</style>

<style lang="scss" scoped>













 

</style>