<template>
    <div class="detailWrap">
        <Row>
            这是详情页面{{nodeDetail}}
            <Row>
                <Col span="6">
                    <label><span class="redStar">*</span>页面ID </label>
                    <Input v-model="pageId" placeholder="输入所属页面ID" clearable style="width: 200px" />
                </Col>
                <Col span="6">
                    <label><span class="redStar">*</span>页面链接 </label>
                    <Input v-model="pageUrl" placeholder="输入当前页面链接" clearable style="width: 200px" />
                </Col>
                <Col span="6"  v-if="nextPageType">
                    <label><span class="redStar">*</span>按钮名称 </label>
                    <Input v-model="buttonId" placeholder="输入要事件ID" clearable style="width: 200px" />
                </Col>
                <Col span="6"  v-if="nextPageType">
                    <label><span class="redStar">*</span>按钮链接 </label>
                    <Input v-model="buttonUrl" placeholder="输入事件链接" clearable style="width: 200px" />
                </Col>
            </Row>
            <Row class="content">
                <Row >
                    <Col span="24">
                        <label><span class="redStar">*</span>标题1 </label>
                        <Input v-model="pageTitle1" placeholder="请输入标题" clearable />
                    </Col>
                </Row>
                <Row>
                    <Col span="24">
                        <label><span class="redStar">*</span>描述 </label>
                        <Input v-model="pageTitle1" type="textarea" :rows="3"placeholder="请输入描述" clearable  />
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
        </Row>
        <Row>
            <Button type="info" size="large" @click="save">保存</Button>
            <Button type="error" size="large" @click="cancel" >取消</Button>
        </Row>
    </div>
</template>
<script>
    export default {
        name:"detailTree",
        data () {
            return {
                pageId:'', 
                pageUrl:'', 
                buttonId:'', 
                buttonUrl:'',
                pageTitle1:'',
                pageTitle2:'',
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
<style>
.detailWrap{
    border:1px solid yellow;
    margin-top:30px;
}
</style>