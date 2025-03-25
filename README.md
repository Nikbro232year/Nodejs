# Nodejs
Basics codes and notes


nodejs
Node js -------->
packege.json take information about the project related
It contains metadata about the project and manages the dependencies and scripts needed to run the application.
and the package lock.json take information about the packages(metadata=name,version,description,main')
nodejs is a single threaded that mean it runs single commands at time

suppose in cases you lost nodemodule how to retireved simply use--> npm install comd
node js is async server 




Express js is framework of a nodejs for making web,api





//application  middleware-->apply on all routes(globly)--it is default for all
but in case of route level middleware are only apply single or more routes  


/*const app = require('./app.js')
console.log(app.z());
 filter use : how to  filter the elements from the arry
in case of == only matched the value not match type
and case of === match type values also
const arr=[1,2,3,4,5,3,3,5];
let result= arr.filter((item)=>{
    //console.log(item)
    return item===3;

})
console.log(result);
core modules global and non globle
create file--->
const fs=require('fs');
console.log("-->",__filename);
fs.writeFileSync("code.txt","Hello !");


const http= require('http');
http.createServer((req,respo)=>{
respo.write("<h1>hello</h1>");
respo.end();
}).listen(4500);

const http= require('http');
function datacontrol(req,respo){
    respo.write("hello");
    respo.end();
}
http.createServer(datacontrol).listen(4500);

// index.js
const http= require('http');
const data = require('./data');
http.createServer((req,resp)=>{
resp.writeHead(500,{'Content-Type':'application\json'});
resp.write(JSON.stringify(data));
resp.end();
}).listen(5000);


console.log(process.argv[0]);

const fs =require('fs');
const input = process.argv;
fs.writeFileSync(input[3],input[4])
if(input[2]=='add'){
    fs.writeFileSync(input[2],input[3])
}else if(input[2]=='remove'){
    fs.unlinkSync(input[3])

}else{
    console.log("invalid")
}




const fs =require('fs');
const input = process.argv;
fs.writeFileSync(input[2],input[3]);

const fs =require('fs');
const path=require('path');

const dirPath=path.join(__dirname,'files');
//for(i=0;i<3;i++ ){
   // fs.writeFileSync(dirPath+"/hello"+i+"txt","a simple text fiel")
//}

fs.readdir(dirPath,(err,files)=>{
    console.log(files);
files.forEach((items)=>{
    console.log(items)
})

})


Crud-->create remove (Create, Read, Update, Delete)


const fs =require('fs');
const path=require('path');
const dirPath=path.join(__dirname,'crud')//directory path
const filePath=`${dirPath}/apple.txt`;//file path

//fs.writeFileSync(filePath,'this is tezt file');
//fs.readFile(filePath,'utf8',(err,item)=>{
  //  console.log(item);
//})

//fs.appendFile(filePath,'add text extra',(err)=>{
 //   if(!err)console.log("file is update");
//});

//fs.rename(filePath,`${dirPath}/fruit.txt`,(err)=>{
   // if(!err)console.log("file is update");
//})

delete the file--->
fs.unlinkSync(`${dirPath}/fruit.txt`);


let a=4;
let b;
let getdata=new Promise((res,rej)=>{
    setTimeout(()=>{
        res(4)
    },2000)
});
getdata.then((data)=>{
    b=data;
    console.log(`answer will be : ${a+b}`)
});
call stack js

framework : Expressjs
npm install express



const express=require('express');
const path=require('path');

const app=express();
const publicpath=path.join(__dirname,'public');
app.use(express.static(publicpath));
app.listen(5000);

const express=require('express');
const path=require('path');

const app=express();
const publicpath=path.join(__dirname,'public');
app.set('view engine','ejs');
app.get('/help',(rep,res)=>{
    res.sendFile(`${publicpath}/about.html`)

})

app.get('*',(_,res)=>{
    res.sendFile(`${publicpath}/help.html`)

})
app.listen(4500);


const express=require('express');
const path=require('path');
const app=express();

const publicpath=path.join(__dirname,'public');

app.set('view engine','ejs');
app.get('/profile',(req,resp)=>{
    const user={
        name:"nikhil ahire",
        email:'ahirenikhil183@gmail.com',
        city:'nashik'
    }
resp.render('profile',{user});
})
app.listen(5000);
const express=require('express');
const reqFilter=require('./middleware');
const middleware = require('./middleware');
const route=express.Router()

const app=express();
route.use(reqFilter);
app.get('/mon',(req,resp)=>{
    resp.send('hello nikhil first router')
})

//application  middleware-->apply on all routes(globly)

//app.use(reqFilter);
//route

//you dont use middleware-->
app.get('/user',(req,resp)=>{
    resp.send('hey it is user side')
})
app.get('/get',(req,resp)=>{
    resp.send('THIS THE GET PAAGE')
})
//you use middleware-->
route.get('/home',(req,resp)=>{
    resp.send('hey it is Home page')
})
route.get('/con',(req,resp)=>{
    resp.send('hey it is con router page')
})
app.use('/',route)
app.listen(4500);


const mongoose=require('mongoose');
const main =async()=>{
    await mongoose.connect('mongodb://localhost:27017/e-com');
    const productSchema=new mongoose.Schema({name:String,price:Number});
}
  /*
// dbConnect().then((resp)=>{
//     resp.find().toArray().then((data)=>{
//         console.log(data)
//     })
// })
  
// console.warn(dbConnect);
// const main=async()=>{
// let data =await dbConnect();
// data=await data.find().toArray();
// console.warn(data);
// }


//  main();

//main();

//model use to conncet nodejs to mongodb
//limitation use mongoose
const ProductModel=mongoose.model('products',productSchema);
let data=new ProductModel({
    name:'lava',
    price:100//validation
});
let result=await data.save();
console.log(result);

}

update in mongodb
const UpdateInB=async()=>{
    const product=mongoose.model('products',productSchema);
   const data=await product.updateOne({name:'yash'},{$set:{name:'Nikhil'}})
   console.log(data);
}

UpdateInB();
}

delete operation

const DeleteInDB=async()=>{
    const product=mongoose.model('products',productSchema);
    let data =await product.deleteOne({name:'yash'});
    console.log(data);
}
DeleteInDB();

const FindInDB=async()=>{
    const product=mongoose.model('products',productSchema);
    let data =await product.find();
    console.log(data);
}
FindInDB();
}
*/
//main();


get put update:

const express=require('express');
require('./config');
const products=require('./product');
const product = require('./product');
const app=express();
// app.use(express.json())
// app.post('/create',async(req,resp)=>{
//     let data=new products(req.body);
//     let result=await data.save();
//     console.log(result);
//     resp.send("Done");
// });

// app.get("/list",async(req,resp)=>{
//     let data=await product.find();
//     resp.send(data)
// });
// app.put("/update/:_id",async(req,resp)=>{

//     let data=await product.updateOne(req.params,{$set:req.body});
//     console.log(data);
    
// });
// app.listen(5000);


app.get("/serach/:key",async(req,resp)=>{
    console.log(req.params.key);
    const data=await products.find(
        {"$or":[{"name":{$regex:req.params.key}},
            {"brand":{$regex:req.params.key}
        }]}
    )
    resp.send(data);
});
app.listen(5000);

product file->

const mongoose =require('mongoose');
const productSchema = new mongoose.Schema({
    
name:String,

brand:String,

price:Number,

category:String

});
module.exports=mongoose.model('products',productSchema);

config file=>

const mongoose=require('mongoose');
mongoose.connect('mongodb://localhost:27017/e-com')

upload file from postman :
const express=require('express');
const multer=require('multer');
const app=express();
const upload=multer({
    storage:multer.diskStorage({
        destination:function(req,file,cb){
            cb(null,"uploads")
        },
        filename:function(req,file,cb){
            cb(null,file.fieldname+"-"+Date.now()+".jpg")
        }
    })

}).single("user_file");
app.post("/upload",upload,(req,resp)=>{
    resp.send('done')
});

app.listen(5000);
