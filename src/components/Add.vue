<template>
  <div class="add">
    <br>
    <div class="add-item container">
      <h2 class="center-align">Create a Bundle</h2>
      <form @submit.prevent="Additem">
        <div class="row">
          <div class="input-field col s8">
            <p class="sub_title">Bundle Title</p>
            <input type="text" name="title" class="validate" v-model="title">
          </div>
          <div class="input-field col s8">
            <p class="sub_title">Price (USD)</p>
            <input type="number" name="price" v-model="price">
          </div>
          <div class="input-field col s12">
            <p class="sub_title">Product Description</p>
            <textarea
              id="textarea2"
              class="materialize-textarea"
              data-length="120"
              v-model="content"
            ></textarea>
          </div>
        </div>
        <div class="row">
          <p class="sub_title">Tags</p>
          <div class="col s4">
            <input type="text" name="tag" v-model="tags[0]">
            <label for="tag">Tag 1</label>
          </div>
          <div class="col s4">
            <input type="text" name="tag" v-model="tags[1]">
            <label for="tag">Tag 2</label>
          </div>
          <div class="col s4">
            <input type="text" name="tag" v-model="tags[2]">
            <label for="tag">Tag 3</label>
          </div>
        </div>
        <!-- Image Area -->
        <div class="divdier"></div>
        <div v-for="(image, index) in this.images" :key="index">
          <a @click.prevent="removeImage(index)">X</a>
          <img :src="image">
        </div>
        <!-- CHOOSE IMAGE -->
        <h2>Upload Image</h2>
        <span class="input-group-text btn btn-primary btn-file" id="basic-addon2">
          <input
            type="file"
            v-on:change="fileUploaded"
            accept="image/png, image/jpeg, image/gif"
            name="input-file-preview"
            multiple
          >
        </span>
        <div>
          <p>{{ loadingText }}</p>
        </div>
        <br>
        <!-- UPLOAD IMAGE -->
        <button>
          <a @click.prevent="uploadImages()">Save Uploaded Images</a>
        </button>
        <div class="row quantity">
          <p class="sub_title">Image Size</p>
          <div class="col s4">S
            <div class="input-field inline">
              <input type="text" v-model="S">
            </div>
          </div>
          <div class="col s4">M
            <div class="input-field inline">
              <input type="text" v-model="M">
            </div>
          </div>
          <div class="col s4">L
            <div class="input-field inline">
              <input type="text" v-model="L">
            </div>
          </div>
        </div>

        <div class="terms">
          <p class="sub_title">Acknowledgements</p>
          <p>
            <label>
              <input type="checkbox" name="terms" value="terms" v-model="terms">
              <span>I agree to the Terms & Conditions.</span>
            </label>
          </p>

          <p>
            <label>
              <input type="checkbox" name="privacy" value="privacy" v-model="privacy">
              <span>I agree to the Privacy Policy</span>
            </label>
          </p>

          <p>
            <label>
              <input type="checkbox" name="license" value="license" v-model="license">
              <span>I agree to the artist's license terms.</span>
            </label>
          </p>
        </div>

        <div class="field center-align btn_box">
          <p v-if="feedback" class="red-text">{{feedback}}</p>
          <button class="btn waves-effect waves-light deep-orange lighten-1">Add Item</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import db from '../firebase/firebaseinit-dev'
import firebase from 'firebase'
import slugify from 'slugify'

const firebaseStorage = firebase.storage();

export default {
  name: 'Add',
  data () {
    return {
      title: null,
      price: null,
      content: null,
      tags: [],
      feedback: null,
      slug: null,
      colors: [],
      S: null,
      M: null,
      L: null,
      wish: false,
      writer: null,
      user: null
    }
  },
  created(){
    let ref= db.collection('users')
      ref.where('user_id','==',firebase.auth().currentUser.uid).get()
      .then(snapshot=>{
          snapshot.forEach(doc => {
              this.user =doc.data(),
              this.user.id = doc.id
          })
          console.log('get current user id')
      })
  },
  methods: {
    Additem(){
          if(this.title && this.price && this.content){
              this.feedback=null
              //create a slug
              this.slug = slugify(this.title, {
                  replacement: '-',
                  remove: /[$*_+~.()'"!\-:@]/g,
                  lower: true
              })
              console.log(this.slug);
 
              db.collection('items').add({
                title: this.title,
                price: this.price,
                content: this.content,
                tags: this.tags,
                colors: this.colors,
                S: this.S,
                M: this.M,
                L: this.L,
                date: Date.now(),
                slug: this.slug,
                writer: this.user.id
              }).then(()=>{
                this.$swal({
                    position: 'center',
                    type: 'success',
                    title: 'Bundle is now in the marketplace!',
                    showConfirmButton: false,
                    timer: 1000
                 })
                 this.$router.push({ name: 'Index'})
              }).catch(err => {
                  console.log(err);
              })

          }else {
              this.feedback= 'something else!'
          }
      },
  }
}
</script>


<style scoped>
.add {
  width: 70%;
  margin: 0 auto;
}
.add h2 {
  color: #ff7657;
  font-size: 1.8em;
  font-weight: bold;
}
.sub_title {
  font-weight: bold;
  color: #ff7657;
}
.divider {
  margin: 40px auto;
}

.btn_box {
  margin-bottom: 40px;
}
</style>

