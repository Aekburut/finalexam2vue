<template>
    <div>
        <h1 class="text-center">Suppliers List</h1>
        <b-table striped hover :items="suppliers" :fields="fields" :per-page="pageSize" :current-page="pageIndex"></b-table>
        <b-pagination :total-rows="suppliers.length" :per-page="pageSize" v-model="pageIndex" />
    </div>
</template>

<script>
import axios from "axios";
export default {
  name: "suppliers",
  data() {
    return {
      message: "suppliers",
      suppliers: [],
      pageSize: 10,
      pageIndex: 1,
      fields: [
        {
          key: "company_name",
          sortable: true
        },
        {
          key: "city",
          sortable: true
        },
        {
          key: "address",
          sortable: true,
          variant: 'danger'
        }
      ]
    };
  },
  mounted() {
    var instance = this;
    axios
      .get("https://finalexam023.herokuapp.com/api/suppliers/")
      .then(function(response) {
        console.log(response);
        instance.suppliers = response.data.data;
      });
  }
};
</script>
