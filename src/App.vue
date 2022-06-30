<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model.trim="uname" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model.number="age1" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="btn">添加/修改</button>
    </div>
    <div>
      <table border="1" cellpadding="10" cellspacing="0">
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="(item, index) in arr" :key="item.id">
          <td>{{ index + 1 }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
          <td>
            <button @click="del">删除</button>
            <button @click="change(index)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      arr: [
        {
          id: 1,
          name: 'Tom',
          age: 19,
          sex: '男',
        },
        {
          id: 2,
          name: 'Som',
          age: 18,
          sex: '女',
        },
        {
          id: 3,
          name: 'Tmw',
          age: 15,
          sex: '男',
        },
      ],
      uname: '',
      age1: 0,
      sex: '男',
    };
  },
  methods: {
    btn() {
      //判断输入框有没有值
      if (this.uname.length === 0 || this.age1.length === 0) {
        return alert('请输入完整的信息');
      }

      this.arr.push({
        // id: this.arr[this.arr.length - 1].id + 1,
        name: this.uname,
        age: this.age1,
        sex: this.sex,
      });
      this.uname = '';
      this.age1 = 0;
    },
    change(index) {
      this.uname = this.arr[index].uname;
    },
  },
};
</script>
