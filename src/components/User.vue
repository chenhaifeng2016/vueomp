<template>
    <div class="table">
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item><i class="el-icon-menu"></i>用户管理</el-breadcrumb-item>
                <el-breadcrumb-item>用户</el-breadcrumb-item>
            </el-breadcrumb>
        </div>

        <el-table :data="tableData" border style="width: 100%">

            <el-table-column prop="username" label="用户名" width="150">            </el-table-column>
          <el-table-column prop="mobilephone" label="手机号" width="160">            </el-table-column>
            <el-table-column prop="email" label="电子邮件" width="230">            </el-table-column>

          <el-table-column prop="realname" label="真实姓名" width="140">            </el-table-column>
            <el-table-column prop="address" label="地址" :formatter="formatter">            </el-table-column>


          <el-table-column prop="createdate" label="注册日期" sortable width="150">            </el-table-column>

            <el-table-column label="操作" width="180">
                <template scope="scope">
                    <el-button size="small"                            @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
                    <el-button size="small" type="danger"                            @click="handleDelete(scope.$index, scope.row)">删除</el-button>
                </template>
            </el-table-column>
        </el-table>

        <div class="pagination">
            <el-pagination  layout="prev, pager, next"  :total="1000"></el-pagination>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                tableData: [{
                    username: 'chenhf',
                  mobilephone: '18049975820',
                  email: 'chenhf@cssweb.sh.cn',
                  realname: '陈海峰',
                  address: '上海市徐汇区肇家浜路755号龙头大厦M3楼',
                    createdate: '2017-03-31'



                },
                  {
                    username: 'chenjf',
                    mobilephone: '18049975820',
                    email: 'chenf@cssweb.sh.cn',
                    realname: '陈建峰',
                    address: '上海市徐汇区肇家浜路755号龙头大厦M3楼',
                    createdate: '2017-03-31'

                }]
            }
        },
        methods: {
            formatter(row, column) {
                return row.address;
            },
            filterTag(value, row) {
                return row.tag === value;
            },
            handleEdit(index, row) {
                this.$message('编辑第'+(index+1)+'行');
            },
            handleDelete(index, row) {
                this.$message.error('删除第'+(index+1)+'行');
            }
        }
    }
</script>
