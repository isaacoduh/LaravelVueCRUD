<template>
    <div class="">
        <!-- <div class="col-md-8">
            <div class="card card-default">
                <div class="card-header">Create Component</div>
                <div class="card-body">
                    I'm the Create Component component.
                </div>
            </div>
        </div> -->
        <h1>Create a Post</h1>
        <form @submit.prevent="addPost">
            <div class="row">
                <div class="col-md-6">
                    <div class="form-group">
                        <label>Post Title:</label>
                        <input type="text" class="form-control" v-model="post.title">
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-md-6">
                    <div class="form-group">
                    <label>Post Body:</label>
                    <textarea class="form-control" v-model="post.body" rows="5"></textarea>
                    </div>
                </div>
            </div>
            <br />
            <div class="form-group">
                <button class="btn btn-primary">Create</button>
            </div>
        </form>
    </div>
</template>
<script>
export default {
    data(){
        return {
            post:{}
        }
    },
    methods: {
        addPost(){
            let uri = 'http://laravuecrud.test/api/post/create';
            this.axios.post(uri, this.post).then((response) => {
                this.$router.push({name: 'posts'});
            })
            console.log(this.post);
        }
    }
}
</script>