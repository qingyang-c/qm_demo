<template>
<div>
  <div class="row">
   <div class="col-md-12 head" >
     <div class="wrapper">     
          <span class="icon-camera">Album</span>
          <span class="icon-menu"></span>
      </div> 
    </div>
  </div>
  <div class="example-box">
    <h3>Album example</h3>
    <h6>Something short and leading about the collection below—its contents,</h6>
    <h6>the creator, etc. Make it short and sweet, but not too short so folks</h6>
    <h6>don't simply skip over it entirely.</h6>
    <div>
    <button type="button" class="btn btn-primary" >
       Main call to action
    </button>
    <button type="button" class="btn btn-default" data-toggle="modal" data-target="#exampleModal">
       secondary
    </button>
    </div>
  </div>
   
  <div class="main-box">
    <div class="wrapper tmargin" > 
      <div class="row" style=" padding-top:20px">
        <div class="col-md-4" v-for="article in articles" :key="article.id" 
        >
          <div class="art">
             <img :src="article.img" alt="">
             
             <div style="padding:5px">
               <div class="textbox">
               <span>{{article.content}}</span>
             </div>

             <div class="bt-box">
               <div> 
                 <button style=" border-right: none; background-color:white">View</button>
                <button style=" background-color:white">Edit</button>
                </div>
              
               <span>{{article.watch}}mins </span>
             </div>
             </div>
             
            
               
             
          </div>

        </div>
 
      </div>
    </div>
   
  </div>
     <div class="footer">
    <span>Album example is  Bootstrap, but please download and customize it for yourself!</span>
    <span>New to Bootstrap? Visit the homepage or read our getting started guide.</span>
    <span>Back to top</span>
    </div>
</div>

 
</template>

<script>
export default {
  name: 'Ablum',
  components: {
    
  },
  created(){
      this.getArticles();
     
  },
  data(){
            return {
                articles: [],
            }
        },
  methods: {
    getArticles(){
      this.axios.get('/getArticles').then(res => {
       this.articles = res.article;
      
      });
    }
  }
}

</script>
<style >
.head{
  height: 40px;
  background-color:rgb(52, 58, 64);
}
.wrapper{
  width: 1000px;
  margin: 0 auto;

}
.icon-camera{
  color: aliceblue;
   line-height: 40px;
   float: left;
}
.icon-menu{
  color: aliceblue;
   line-height: 40px;
   font-size: 30px;
   float: right;
  
}
.example-box{
  height: 300px;
  display: flex;
  flex-direction: column;
  justify-content:center;
}
.btn-default{
  background-color: rgb(108, 117, 125);
}
.btn-primary{
 margin-left: -50px;
 margin-right: 5px;
}
.main-box{
  background-color:rgb(228, 228, 228);
  height: 1350px;
}
.tmargin{
  margin-top: 20px;
}
.art{
  height: 400px;
  margin-top: 20px;
  background: white  ;
  overflow: hidden;
  text-align: left;
}
.textbox{
  height: 150px;
}
.bt-box{
  display: flex;
  justify-content:space-between;
 
}
.footer{
  height: 200px;
  background-color: #fff;
  line-height: 200px;
}
</style>