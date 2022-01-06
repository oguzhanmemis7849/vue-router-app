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
          <th scope="col">Açıklama</th>
          <th scope="col">Sil</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(bookmark, index) in bookmarkList" :key="bookmark.id">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ bookmark.title }}</td>
          <td>
            <!-- :href ==>> bind edilme işlemi -->
            <a :href="bookmark.url" target="_blank">{{ bookmark.url }}</a>
          </td>
          <td>
            {{ bookmark.description }}
          </td>
          <td>
            <button @click="deleteItem(bookmark)" class="btn btn-sm btn-danger">Sil</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data(){
    return {
      bookmarkList : []
    }
  },
  created(){
    this.$appAxios.get("/bookmarks").then(bookmarks_list_response => {
      this.bookmarkList = bookmarks_list_response.data || [];
      console.log(bookmarks_list_response);
    })
  },
  methods:{
    //Silme işlemi(id'sine göre)
    deleteItem(bookmark) {
      // console.log('bookmark :>> ', bookmark);
      this.$appAxios.delete(`/bookmarks/${ bookmark.id }`).then(delete_response => {
        console.log(delete_response);
        if(delete_response.status === 200){ // doğru çalışıyorsa bookmarkListin içinden sildiğim id dışında kalanları getir.
          this.bookmarkList = this.bookmarkList.filter(b => b.id != bookmark.id)
        }
      })
    }
  }
};
</script>

<style></style>
