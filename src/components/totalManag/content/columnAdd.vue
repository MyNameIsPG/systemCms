<template>
    <div class="__columnAdd">
        <el-card class="box-card">
            <div slot="header" class="clearfix">
                <span>新增栏目</span>
            </div>
            <div class="addFromListBox">
                <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
                    <el-form-item label="栏目名称" prop="name" class="form-control">
                        <el-input v-model="ruleForm.name" placeholder="请输入文章名称"></el-input>
                    </el-form-item>
                    <el-form-item label="所属社区" prop="name">
                        <el-select v-model="ruleForm.region" placeholder="请选择所属社区">
                            <el-option label="西湖街道办" value="shanghai"></el-option>
                            <el-option label="八方小区" value="beijing"></el-option>
                        </el-select>
                    </el-form-item>
                    <el-form-item label="描述" prop="desc">
                        <el-input type="textarea" v-model="ruleForm.desc" placeholder="写点什么吧！"></el-input>
                    </el-form-item>
                    <el-form-item>
                        <el-button type="primary" @click="submitForm('ruleForm')">提交</el-button>
                        <el-button @click="resetForm('ruleForm')">重置</el-button>
                    </el-form-item>
                </el-form>
            </div>
        </el-card>
    </div>
</template>

<script>
export default {
  	data() {
		return {
			ruleForm: {
				name: "",
				region: "",
				date1: "",
				date2: "",
				delivery: false,
				type: [],
				resource: "",
				desc: ""
			},
			rules: {
				name: [
					{ required: true, message: "请输入文章内容", trigger: "blur" },
					{ min: 2, max: 64, message: "长度在 3 到 5 个字符", trigger: "blur" }
				],
				region: [
					{ required: true, message: "请选择活动区域", trigger: "change" }
				],
			}
		};
	},
	methods: {
		submitForm(formName) {
			this.$refs[formName].validate(valid => {
				if (valid) {
				alert("submit!");
				} else {
				console.log("error submit!!");
				return false;
				}
			});
		},
		resetForm(formName) {
			this.$refs[formName].resetFields();
		},
		getUEContent() {
            let content = this.$refs.ue.getUEContent(); // 调用子组件方法
            this.$notify({
                title: '获取成功，可在控制台查看！',
                message: content,
                type: 'success'
            });
        },
        getUEContentTxt() {
            let content = this.$refs.ue.getUEContentTxt(); // 调用子组件方法
            this.$notify({
                title: '获取成功，可在控制台查看！',
                message: content,
                type: 'success'
            });
        }
	}
};
</script>

<style lang="stylus">
.__columnAdd {
	.addFromListBox {
		width 960px;
		.form-control {
			width 60%;
		}
		.el-textarea {
			textarea {
				height 90px;
			}
		}
	}
}
</style>
