<template>
  <div>

    <h1>{{ msg }}</h1>
    <table class="a">
      <tr  v-for="index in syk" :key="index.id">
        <td class="a">{{index.id}}</td>
        <td class="a">{{index.IMEI}}</td>
        <td class="a">{{index.device}}</td>
        <td class="a">{{index.message}}</td>
        <td class="a">{{index.tel}}</td>
      </tr>
    </table>
    <button>显示</button>
 </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
    data() {
    return {
      syk: ""
    };
  },

  created() {
    this.axios
      .get("http://localhost:60020/all")
      .then(response => {
        console.log(response);
        this.syk = response.data.data;
        console.log(this.syk);
      })
      .catch(error => {
        console.log(error);
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.a {
  border: 1px solid black;
}
</style>
