<template>
    <div>
        <Row>
            <Col span="4"><Tree :data="data1" @on-select-change="getCheckedNodes"></Tree></Col>
            <Col span="20">
                <list :showEditButton =" showEditButton" :data2="data2" :nodeDetail="nodeDetail"></list>
                <addTree :nodeDetail="nodeDetail"></addTree>
                <detailTree :nodeDetail="nodeDetail"></detailTree>
                <editTree></editTree>
            </Col>
        </Row>
    </div>
</template>
<script>
    import addTree from '../components/Marriage/consultation/consultation-addTree.vue'
    import detailTree from '../components/Marriage/consultation/consultation-detailTree.vue'
    import editTree from '../components/Marriage/consultation/consultation-editTree.vue'
    import list from '../components/Marriage/consultation/consultation-list.vue'
    export default {
        name:"about",
        components: {
            addTree,
            detailTree,
            editTree,
            list
        },
        data () {
            return {
                nodeDetail:'parent 1',
                showEditButton:false ,
                data1: [
                    {
                        title: 'parent 1',
                        expand: true,
                        selected: true,
                        children: [
                            {
                                title: 'parent 1-1',
                                expand: false,
                                children: [
                                    {
                                        title: 'leaf 1-1-1',
                                        expand: false,
                                        children: [
                                            {
                                                title: 'leaf 1-1-1-1',
                                                expand: false
                                            },
                                            {
                                                title: 'leaf 1-1-1-2',
                                                expand: false
                                            }
                                        ]
                                    },
                                    {
                                        title: 'leaf 1-1-2'
                                    }
                                ]
                            },
                            {
                                title: 'parent 1-2',
                                expand: false,
                                children: [
                                    {
                                        title: 'leaf 1-2-1'
                                    },
                                    {
                                        title: 'leaf 1-2-1'
                                    }
                                ]
                            }
                        ]
                    }
                ],
                data2: [
                    {
                        name: 'John Brown',
                        age: 18,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03'
                    },
                    {
                        name: 'Jim Green',
                        age: 24,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joe Black',
                        age: 30,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Jon Snow',
                        age: 26,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    }
                ]
            }
        },
        methods:{
            getCheckedNodes(o,v){
                console.log(o,v)
                console.log(v.title)
                this.nodeDetail = v.title
                v.expand=true
                if(v.hasOwnProperty("children")){
                    console.log("有子代")
                    // v.children.forEach((item, index) => {
                    //     item.expand=false
                    //     if(item.hasOwnProperty("children")){
                    //         console.log(index)
                    //         console.log(item.title + "有孙代")
                    //     }else{
                    //         console.log(index)
                    //         console.log("没有孙代")
                    //         this.hasGrandson = false
                    //     }

                    // })
                    for(let i = 0;i < v.children.length;i++){
                        if(v.children[i].hasOwnProperty("children")){
                            console.log(v.children[i].title + "有孙代")
                            this.showEditButton = false
                            return
                        }else{
                            this.showEditButton = true
                            console.log("没有孙代")
                        }
                    }
                }else{
                    this.showEditButton = true
                    console.log("这个不能点击")
                    v.disabled=true
                }
            },
            
        }
    }
</script>
<style>
.ivu-row{
    margin:20px 0px;
}
.ivu-table-wrapper{
    margin-top:20px;
}
</style>
