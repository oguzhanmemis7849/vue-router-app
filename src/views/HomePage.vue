<template>
  <div class="card border b-2">
    <div class="d-flex justify-content-end">
      <button class="btn btn-sm btn-primary m-2" @click="$router.push({ name:'NewBookmark' })">+ Yeni Ekle</button>
    </div>
    <table class="table table-striped table-hover">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Başlık</th>
          <th scope="col">URL</th>
          <th scope="col">Sil</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="i in 10" :key="i">
          <th scope="row">1</th>
          <td>Vue3 Dokumantasyon</td>
          <td>https://v3.vuejs.org</td>
          <td>
            <button class="btn btn-sm btn-danger">Sil</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {};
</script>

<style></style>
