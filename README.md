# Restful-API
'''
const express = require("express");
const mongoose= require("mongoose");
const ejs= require("ejs");
const bodyparser= require("body-parser");
const app =express();
app.set('veiw engine','ejs');
app.use(bodyparser.urlencoded({extended:true}));
app.use(express.static("public"));
mongoose.connect('mongodb+srv://Adminchirag:test123@cluster0.h8fqm.mongodb.net/todolistDB?retryWrites=true&w=majority', {useNewUrlParser: true});
const articleSchema =mongoose.Schema({
  title:String,
  content:String
});
const Article = mongoose.model("Article",articleSchema );
/////////////////////////////////////////// Requests Targetting All Articles////////////////////////////
app.route("/articles")
.get(function(req, res){
  Article.find(function(err, foundArticles){
if(!err){
  res.send(foundArticles);
}else{
  res.send(err);
}
});
})
.post(function(req,res){
  const newArticle = new Article({
    title:req.body.title,
    content:req.body.content
  });
  newArticle.save(function(err){
    if(!err){
      res.send("sucessful");
    }else{
      console.log(err);
    }
  });
})
.delete(function(req, res){
  Article.deleteMany(function(err){
    if(!err){
      console.log("sucessfull");
    }else{
      console.log(err);
    }
  });
});
/////////////////////////////////////////// Requests Targettiting A specific Article////////////////////////////
app.route("/articles/:articleTitle")
.get(function(req, res){
  let Title =req.params.articleTitle;
   Article.findOne({title:Title},function(err , foundArticles){
     if(foundArticles){
       res.send(foundArticles);
     }else{
       res.send("no article found");
     }
   });
});


app.listen(3000,function(){
  console.log("serve started on port 3000");
});
'''
