## Vue-Core-Image-Upload 
a vue plugin for image upload and crop ( Support 📱 IE9+)

Vue.js>=2.0,
this project will be merged to the [project](https://github.com/Vanthink-UED/vue-core-image-upload)

<img width="360" src="./shots/CORE-IMAGE-UPLOAD-LOGO.png" />

if you use vue.js(1.x), you should go [here](https://github.com/Vanthink-UED/vue-core-image-upload)

### Install

``` bash
npm i vue2.x-core-image-upload --save
```

Code Example (ES6)
``` js
import VueCoreImageUpload  from './vue.core.image.upload.vue';

new Vue({
  el: '#app',
  components: {
    'vue-core-image-upload': VueCoreImageUpload
  },
  data: {
    src: 'http://img1.vued.vanthink.cn/vued0a233185b6027244f9d43e653227439a.png',
  },
  methods: {
    imageUploaded(res) {
      if (res.errcode == 0) {
        this.src = 'http://img1.vued.vanthink.cn/vued751d13a9cb5376b89cb6719e86f591f3.png';
      }
    }
  },

});
```

Use Script(ES5)
```js

<script src="./node_modules/vue-core-image-upload/index.js"></script>
...
<script>
    var MyComponent = Vue.extend(VueCoreImageUpload);
    new Vue({
      el: '#app',
      components: {
        'vue-core-image-upload': MyComponent
      },
      data: {
        src: 'http://img1.vued.vanthink.cn/vued0a233185b6027244f9d43e653227439a.png',
      },
      methods: {
        imageUploaded: function(res) {
          if (res.errcode == 0) {
            this.src = 'http://img1.vued.vanthink.cn/vued751d13a9cb5376b89cb6719e86f591f3.png';
          }
        }
      },
    });
</script>
```

``` html
<vue-core-image-upload v-bind:class="['pure-button','pure-button-primary','js-btn-crop']" v-bind:crop="false" url="./crop.php" extensions="png,gif,jpeg,jpg" v-on:imageuploaded="imageuploaded"></vue-core-image-upload>
```

[Demo] (http://vanthink-ued.github.io/vue-core-image-upload/upload.html)

### Options

| Props        | Type         | Example  | Description  |
| ------------- |:----------| ---------|--------------|
| url     | String | '/crop.php' | your server url |
| text      | String      |  'Upload Image' | the text you want to show |
| inputOfFile | String     |   'file' | upload file form name |
| extensions | String   |    'png,jpg,gif' | limit the file type |
| crop | Boolean   |   true | if need crop image |
| cropRatio | String   |   '1:1' | limit the cropped image shape|
| cropBtn | Object   |   {ok:'Save','cancel':'Give Up'} | the text of crop button|
| maxFileSize | Number   |   10485760(10M) | limit the file size|
| maxWidth | Number   |   150 | limit the width of your image you cropped|
| maxheight | Number   |   150 | limit the height of your image you cropped|
| inputAccept | string   |  'image/*' / 'image/jpg,image/jpeg,image/png' |  the image file of accept type |

### events


``` js
//finish image uload
imageuploaded(res) {
  if (res.errcode == 0) {
    this.src = 'http://img1.vued.vanthink.cn/vued751d13a9cb5376b89cb6719e86f591f3.png';

  }
}


// uploading image
imageuploading(res) {
  console.info('uploading');
}

// handle some error like ajax not working
errorhandle(err) {
  console.error(err);
}
```
``` html
<vue-core-image-upload v-bind:crop="false" url="./crop.php" v-on:imageuploaded="imageuploaded" v-on:errorhandle="func"></vue-core-image-upload>
```

### Server Crop Arguments

If you crop a image , your crop will send a request to your server with some crop arguments;

                        
<img src="./shots/vuedba0ed377b88fc84d51026310efcb255b.png" />


+ `toCropImgX`: the distance of cropbox to the image left;
+ `toCropImgY`: the distance of cropbox to the image top
+ `toCropImgW`: the width of cropbox
+ `toCropImgH`: the height of cropbox
+ `maxWidth`: the maxium width of your target image 
+ `maxHeight`: the maxium height of your target image 
If you want to change the crop window style , you should write your own css files.

### MIT Liscense 
