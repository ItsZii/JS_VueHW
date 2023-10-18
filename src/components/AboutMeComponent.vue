<template>
  <div>
    <h1>ABOUT ME</h1>
    <div class="user-info">
      <h3>Name: <span class="label"> {{ user.name }}</span></h3>
      <h3>Surname: <span class="label">{{ user.surname }}</span> </h3>
      <h3>Code: <span class="label"> {{ user.code }}</span></h3>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: "Ieva Madara",
        surname: "Glavecka",
        code: "IT21043"
      }
    };
  }
};
</script>

<style scoped>
h1, .label {
  color: white; 
}
</style>
