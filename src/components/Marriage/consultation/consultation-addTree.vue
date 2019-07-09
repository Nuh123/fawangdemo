<template>
    <div class="addWrap">
       这是添加页面{{nodeDetail}}
        <Row>
            <Col span="6">
                <label><span class="redStar">*</span>所属页面ID </label>
                <Input v-model="pageId" placeholder="输入所属页面ID" clearable style="width: 200px" />
            </Col>
            <Col span="6">
                <label><span class="redStar">*</span>当前页面链接 </label>
                <Input v-model="pageUrl" placeholder="输入当前页面链接" clearable style="width: 200px" />
            </Col>
            <Col span="6"  v-if="nextPageType">
                <label><span class="redStar">*</span>事件ID </label>
                <Input v-model="eventId" placeholder="输入要事件ID" clearable style="width: 200px" />
            </Col>
            <Col span="6"  v-if="nextPageType">
                <label><span class="redStar">*</span>事件链接 </label>
                <Input v-model="eventUrl" placeholder="输入事件链接" clearable style="width: 200px" />
            </Col>
        </Row>
        <Row class="content">
             <Row >
                <Col span="24">
                    <label><span class="redStar">*</span>标题 </label>
                    <Input v-model="pageTitle" placeholder="请输入标题" clearable />
                </Col>
            </Row>
            <Row>
                <Col span="24">
                    <label><span class="redStar">*</span>事件可视化设置 </label>
                    <Select v-model="eventVsiable" placeholder="请选择状态"  >
                        <Option v-for="item in eventVsiableArry" :value="item.value" :key="item.value">{{ item.label }}</Option>
                    </Select>
                </Col>
            </Row>
            <Row>
                <Col span="24">
                    <label><span class="redStar">*</span>是否链接 </label>
                    <Select v-model="isUrl" placeholder="请选择状态">
                        <Option v-for="item in isUrlArry" :value="item.value" :key="item.value">{{ item.label }}</Option>
                    </Select>
                </Col>
            </Row>
            <Row>
                <Col span="24">
                    <label><span class="redStar">*</span>下级页面类型 </label>
                    <Select v-model="nextPageType" placeholder="请选择状态">
                        <Option v-for="item in nextPageTypeArry" :value="item.value" :key="item.value">{{ item.label }}</Option>
                    </Select>
                </Col>
            </Row>
            <Row v-if="nextPageType">
                <Col span="24">
                    <label><span class="redStar">*</span>下级页面标题 </label>
                    <Select v-model="nextPageTitle" placeholder="请选择状态">
                        <Option v-for="item in nextPageTitleArry" :value="item.value" :key="item.value">{{ item.label }}</Option>
                    </Select>
                </Col>
            </Row>
        </Row>
        <Row>
            <Button type="info" size="large" @click="save">保存</Button>
            <Button type="error" size="large" @click="cancel" >取消</Button>
        </Row>
    </div>
</template>
<script>
    export default {
        name:"addTree",
        data () {
            return {
               pageId:'', 
               pageUrl:'', 
               eventId:'', 
               eventUrl:'',
               pageTitle:'',
               eventVsiable:'',
               isUrl:'',
               nextPageType:'',
               nextPageTitle:'',
               eventVsiableArry: [],
               isUrlArry:[],
               nextPageTypeArry:[],
               nextPageTitleArry:[]
            }
        },
        props:[
            'nodeDetail'
        ],
        methods:{
            save(){
                console.log("点击保存按钮")
            },
            cancel(){
                console.log("点击取消按钮")
            }
        }
    }
</script>
<style >
.addWrap{
    border:1px solid red;
    margin-top:30px;
}
label .redStar{
    color:red;
    margin-right:5px;
}
.content .ivu-col label{
    float:left;
    width:150px;
    text-align:right;
    margin-right:10px;
}
.content .ivu-col .ivu-select{
    float:left;
    width:30%;
}
.content .ivu-col .ivu-input-wrapper{
    float:left;
    width:80%;
}
.ivu-row .ivu-btn{
    margin-left:20px;
}
</style>