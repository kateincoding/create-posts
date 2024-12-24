<template>
    <div class="mt-100 layout-column align-items-center justify-content-center">
      <h1>Blog Posts</h1>
      <div>
        <button data-testid="new-button" @click="openCreatePost = true">New Post</button>
      </div>
  
      <!-- use this code template. -->
  
      <div v-if="openCreatePost" class="card flex layout-column px-30">
        <h2 class="text-center" v-if="editIndex === null">Create New Post</h2>
        <h2 class="text-center" v-else>Edit Post</h2>
        <input data-testid="new-title" v-model="newPost.title" type="text" placeholder="Title"><br>
        <textarea data-testid="new-content" v-model="newPost.content" placeholder="Content"></textarea><br>
        <input data-testid="new-author" v-model="newPost.author" type="text" placeholder="Author"><br>
        <button data-testid="save-button" class="mx-auto" @click="createPost">Save</button>
      </div>
  
      <div 
        v-for="(post, index) in posts"
        :key="index"
        class="flex layout-column align-items-center justify-content-center">
        <div class="card px-50">
          <h2 data-testid="title">Title : {{ post.title }}</h2>
          <p data-testid="content">Content : {{ post.content }}</p>
          <p data-testid="author">Author : {{  post.author }}</p>
        </div>
        <div>
          <button data-testid="edit-button" @click="editPost(index)">Edit</button>
          <button data-testid="delete-button" @click="deletePost(index)">Delete</button>
        </div>
      </div> 
  
     
      
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        openCreatePost: false,
        posts: [],
        newPost: {
          title: "",
          content: "",
          author: "",
        }
      };
      
    },
    methods: {
      cleanForm(){
        this.newPost = {
          title: "",
          content: "",
          author: "",
        }
        this.openCreatePost = false;
        this.editIndex = null;
      },
      createPost(){
        if(this.newPost.title == "" || this.newPost.content == "" || this.newPost.author == "")
          alert("Please fill in all fields")
        else {
          if (this.editIndex !== null){
            this.posts[this.editIndex] = {...this.newPost};
          } else {
            // create
            this.posts.push({...this.newPost})
          }
          
        }
        this.cleanForm()
      },
      editPost(index){
        this.openCreatePost = true;
        this.editIndex = index;
        this.newPost = {...this.posts[index]};
      },
      deletePost(index){
        this.posts.splice(index,1);
      }
    }
  };
  </script>
  
  <style scoped>
    
    h1 {
      font-size: 24px;
    }
    h2 {
      font-size: 20px;
    }
    input[type="text"],
    textarea {
      padding: 5px;
      margin-bottom: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    input[type="text"]:focus,
    textarea:focus {
      outline: none;
      border-color: dodgerblue;
    }
  </style>