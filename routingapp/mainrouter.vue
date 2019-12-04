<template>
  <div>
    <table class="table table-striped table-bordered">
      <tr>
        <td>
          <router-link to="/">Product List</router-link>
        </td>
        <td>
          <router-link to="/productcreate">Create Product</router-link>
        </td>
      </tr>
    </table>
    <br>
    <router-view></router-view>
  </div>
</template>

<script>
  
export default {
  name: "MainRouterComponent"
};
</script>