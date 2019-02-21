<template>
  <div >
      <h1>Edit Post</h1>
      <form @submit.prevent="updatePost">
          <div class="row">
              <div class="col-md-6">
                  <div class="form-group">
                      <label for="">Post Title:</label>
                      <input type="text" class="form-control" v-model="post.title">
                  </div>
              </div>
          </div>
          <div class="row">
              <div class="col-md-6">
                  <div class="form-group">
                      <label for="">Post Body:</label>
                      <textarea class="form-control" v-model="post.body" rows="10"></textarea>
                  </div>
              </div>
          </div>
          <br/>
          <div class="form-group">
              <button class="btn btn-primary">Update</button>
          </div>
      </form>
      <!-- <div class="col-md-8">
          <div class="card card-default">
              <div class="card-header">Edit Component</div>

              <div class="card-body">
                  I'm an Edit component.
              </div>
          </div>
      </div> -->
  </div>
</template>

<script>
    export default {
        data(){
            return {
                post: {}
            }
        },
        created(){
            let uri = `http://laravuecrud.test/api/post/edit/${this.$route.params.id}`;
            this.axios.get(uri).then((response) => {
                this.post = response.data;
            });
        },
        methods: {
            updatePost(){
                let uri = `http://laravuecrud.test/api/post/update/${this.$route.params.id}`;
                this.axios.post(uri, this.post).then((response) => {
                    this.$router.push({name: 'posts'});
                });
            }
        }
    }
</script>