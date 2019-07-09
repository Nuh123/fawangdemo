<template>
    <div class="listWrap">
        <p>{{nodeDetail}}</p>
        <Row>
            <Col span="6">
                <label>创建时间： </label>
                <DatePicker type="daterange"  @on-ok="changeTime" confirm show-week-numbers placeholder="Select datee" style="width: 200px"  v-model="searchTime"></DatePicker>
            </Col>
            <Col span="5">
                <label>状态： </label>
                <Select v-model="model1" placeholder="请选择状态" style="width:150px">
                    <Option v-for="item in cityList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                </Select>
            </Col>
            <Col span="5">
                <label>创建人： </label>
                <Input v-model="valuePeople" placeholder="输入要搜索的创建人" clearable style="width: 200px" />
            </Col>
            <Col span="5">
                <label>标题： </label>
                <Input v-model="valueTitle" placeholder="输入要搜索的标题" clearable style="width: 200px" />
            </Col>
            <Col span="3">
                <Button type="info" @click="searchResult">查询</Button>
            </Col>
        </Row>
        <Row type="flex" justify="start">
            <Button type="info" @click="addTree">新增</Button>
        </Row>
        <Table border stripe :loading="loading" :columns="columns1" :data="data2"></Table>
    </div>
</template>
<script>
    export default {
        name:"editTree",
        data () {
            return {
                showlist:true,
                valueTitle:"",
                valuePeople:"",
                searchTime:['2019-06-01', '2019-07-15'],
                loading :false,
                model1: '',
                columns1: [
                    {
                        title: '标题',
                        key: 'name',
                        align:'center'
                    },
                    {
                        title: '创建人',
                        key: 'age',
                        align:'center'
                    },
                    {
                        title: '创建时间',
                        key: 'address',
                        align:'center'
                    },
                    {
                        title: '状态',
                        key: 'date',
                        align:'center'
                    },
                    {
                        title: '操作',
                        key: 'action',
                        align: 'center',
                        render: (h, params) => {
                            if(this.showEditButton){
                                // console.log("有编辑按钮")
                                return h('div', [
                                    h('Button', {
                                        props: {
                                            type: 'primary',
                                            size: 'small'
                                        },
                                        style: {
                                            marginRight: '5px'
                                        },
                                        on: {
                                            click: () => {
                                                this.show(params)
                                            }
                                        }
                                    }, '查看'),
                                    h('Button', {
                                        props: {
                                            type: 'primary',
                                            size: 'small'
                                        },
                                        style: {
                                            marginRight: '5px',
                                        },
                                        on: {
                                            click: () => {
                                                this.edit(params)
                                            }
                                        }
                                    }, '编辑'),
                                    h('Button', {
                                        props: {
                                            type: 'error',
                                            size: 'small'
                                        },
                                        on: {
                                            click: () => {
                                                this.remove(params)
                                            }
                                        }
                                    }, '删除')
                                ]);
                            }else{
                                // console.log("没有编辑按钮")
                                return h('div', [
                                    h('Button', {
                                        props: {
                                            type: 'primary',
                                            size: 'small'
                                        },
                                        style: {
                                            marginRight: '5px'
                                        },
                                        on: {
                                            click: () => {
                                                this.show(params)
                                            }
                                        }
                                    }, '查看'),
                                    h('Button', {
                                        props: {
                                            type: 'error',
                                            size: 'small'
                                        },
                                        on: {
                                            click: () => {
                                                this.remove(params)
                                            }
                                        }
                                    }, '删除')
                                ]);
                            }
                        }
                    }
                ],
                
                cityList: [
                    {
                        value: 'New York',
                        label: 'New York'
                    },
                    {
                        value: 'London',
                        label: 'London'
                    },
                    {
                        value: 'Sydney',
                        label: 'Sydney'
                    },
                    {
                        value: 'Ottawa',
                        label: 'Ottawa'
                    },
                    {
                        value: 'Paris',
                        label: 'Paris'
                    },
                    {
                        value: 'Canberra',
                        label: 'Canberra'
                    }
                ]
            }
        },
        props:[
            'showEditButton',
            'data2',
            'nodeDetail'
        ],
        methods:{
            show (params) {
                console.log(params.row.date)
                this.$Modal.info({
                    title: 'User Info',
                    content: `Name：${this.data2[params.index].name}<br>Age：${this.data2[params.index].age}<br>Address：${this.data2[params.index].address}`
                })
            },
            edit(params){
                console.log(params.row.date)
                点击编辑
            },
            remove (params) {
                console.log(params.row.date+"点击删除")
                this.data2.splice(params.index, 1);
            },
            changeTime(){
                console.log("这始时间"+this.searchTime)
                console.log(this.searchTime)
            },
            searchResult(){
                console.log("查询了")
            },
            addTree(){
                console.log("新增了")
            }
        }
    }
</script>
<style>
.listWrap{
    border:1px solid blue;
    margin-top:30px;
}
</style>