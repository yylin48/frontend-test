<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-10">
        <h1>User List</h1>
        <hr><br><br>
        <button type="button" class="btn btn-success btn-sm">Add User</button>
        <br><br>
        <table class="table table-hover">
          <thead>
            <tr>
              <th scope="col">Name</th>
              <th scope="col">Keyword</th>
              <th scope="col">URL</th>
              <th scope="col">Line ID</th>
              <th scope="col">Category</th>
              <th></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(user) in list" :key="user.name">
              <td>{{ user.name }}</td>
              <td>{{ user.keyword }}</td>
              <td>{{ user.url }}</td>
              <td>{{ user.line_id }}</td>
              <td>{{ user.category }}</td>
              <td>
                <button type="button" class="btn btn-warning btn-sm">Update</button>
                <button type="button" class="btn btn-danger btn-sm">Delete</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios';

export default {
  name: 'List',
  data() {
    return {
      list: [],
    };
  },

  methods: {
    getList() {
      const path = 'http://ec2-3-112-191-59.ap-northeast-1.compute.amazonaws.com/show';
      axios.get(path)
        .then((res) => {
          this.list = res.data.data;
          console.log(res);
        })
        .catch((error) => {
          // eslint-disable-next-line
          console.error(error);
        });
    },
  },
  created() {
    this.getList();
  },
};
</script>
