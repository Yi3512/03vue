<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model.trim="name" placeholder="请输入姓名" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model.number="age" placeholder="'请输入年龄" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="btn">{{ idEdit ? '修改' : '添加' }}</button>
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
        <tr v-for="item in arr" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
          <td>
            <button @click="del(item.id)">删除</button>
            <button @click="change(item.id)">编辑</button>
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
          id: 100,
          name: 'Tom',
          age: 19,
          sex: '男',
        },
        {
          id: 101,
          name: 'Som',
          age: 18,
          sex: '女',
        },
        {
          id: 102,
          name: 'Tmw',
          age: 15,
          sex: '男',
        },
      ],
      name: '',
      age: '',
      sex: '男',
      idEdit: false,
      currend: 0,
    };
  },
  methods: {
    btn() {
      //判断输入框有没有值
      if (this.name == '' || this.age == '') {
        return alert('请输入完整的信息');
      }

      this.arr.push({
        id: this.arr[this.arr.length - 1]
          ? this.arr[this.arr.length - 1].id + 1
          : 100,
        name: this.name,
        age: this.age,
        sex: this.sex,
      });
      this.name = '';
      this.age = 0;
      this.sex = '男';
    },
    change(id) {
      let index = this.arr.findIndex((obj) => obj.id === id);
      this.name = this.arr[index].name;
      this.age = this.arr[index].age;
      this.sex = this.arr[index].sex;
    },
    del(id) {
      let index = this.arr.findIndex((obj) => obj.id === id);
      this.arr.splice(index, 1);
    },
  },
};
</script>
